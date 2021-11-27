**Use state of art libraries for Approximate nearest neighbor search for your favorite data set**

We can split ANN algorithms into mostly three distinct categories: trees(Annoy), hashes(LSH), and graphs(HSNW).

**LHS(Locality-sensitive hashing):**
LSH is a hashing based algorithm to identify approximate nearest neighbors.
Locality Sensitive hashing is a technique to enable creating a hash or putting items in buckets such similar items are in the same bucket (same hash) with high probability and Dissimilar items are in different buckets – i.e dissimilar items are in the same bucket with low probability.

**Product Quantization:**
Quantization is a technique to reduce dataset size (from linear) by defining a function (quantizer) that encodes our data into a compact approximated representation.
In Product Quantization we can increase drastically the number of centroids by dividing each vector into many vectors and run our quantizer on all of these and thus improves accuracy. 

**Exhaustive Search:**
Construct a table with the calculated distance between each sub-vector and each of the centroids for that sub-vector. Calculating approximate distance values for each of the vectors in the dataset, we just use those centroids id’s to look up the partial distances in the table and sum those up!

**Trees Based ANN ( Ex: Annoy - Approximate Nearest Neighbors Oh Yeah):**
They construct forests (collection of trees) as their data structure by splitting the dataset into subsets. Each tree is constructed in the following way, we pick two points at random and split the space into two by their hyperplane, we keep splitting into the subspaces recursively until the points associated with a node is small enough. 

_Summary:_ Annoy's algorithm

_Preprocessing time:_
Build up a bunch of binary trees. For each tree, split all points recursively by random hyperplanes.

_Query time:_
Insert the root of each tree into the priority queue
Until we have _search_k _candidates, search all the trees using the priority queue
Remove duplicate candidates
Compute distances to candidates
Sort candidates by distance
Return the top ones

**HNSW (Hierarchical Navigable Small Worlds):**
It is a proximity graph, in which two vertices are linked based on their proximity (closer vertices are linked) — often defined in Euclidean distance.
There is a significant leap in complexity from a ‘proximity’ graph to ‘hierarchical navigable small world’ graph. two fundamental techniques that contributed most heavily to HNSW: the probability skip list, and navigable small world graphs.
