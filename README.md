// Sample webpages
const webpages = [
  {
    title: "Webpage 1",
    content: "This is the content of webpage 1. It contains words like sample, search, and engine."
  },
  {
    title: "Webpage 2",
    content: "Webpage 2 is a page with some content. It has words like code, snippet, and example."
  },
  {
    title: "Webpage 3",
    content: "Another webpage with more content. Keywords for this page include JavaScript, best practices, and troubleshooting."
  }
];

// Sample keywords
const keywords = ["sample", "search", "engine", "code", "snippet", "example", "JavaScript", "best practices", "troubleshooting"];

// Function to perform a search
function search(query) {
  // Split the query into words
  const queryWords = query.split(" ");

  // Initialize scores for each webpage
  const scores = webpages.map(() => 0);

  // Check if each word is present in the keywords or content of each webpage
  for (const word of queryWords) {
    for (let i = 0; i < webpages.length; i++) {
      const webpage = webpages[i];

      // Check if the word is present in the keywords
      if (keywords.includes(word)) {
        if (webpage.keywords.includes(word)) {
          scores[i] += 1;
        }
      } else {
        // Check if the word is present in the content
        if (webpage.content.includes(word)) {
          scores[i] += 1;
        }
      }
    }
  }

  // Sort the webpages by their score and return the top results
  const sortedWebpages = webpages.sort((a, b) => scores[webpages.indexOf(b)] - scores[webpages.indexOf(a)]);

  return sortedWebpages.slice(0, 5);
}

// Example usage
const results = search("JavaScript best practices");
console.log(results);
