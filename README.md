# HW4

1. Import Libraries: handling arrays (NumPy), reading and displaying images (scikit-image), and plotting (matplotlib) are imported.

2. Image Loading: Utilizing skimage's `io.imread` function, an image -'image.png' is loaded from the disk. The image is then displayed in its original form using `skimage.io.imshow` followed by `plt.show()` to pop up a window showing the image through matplotlib's interface.

3. Normalization: The pixel values of the image range from 0 to 255 for each color channel (red, green, and blue), are normalized to the range of 0 to 1 by dividing by 255. This normalization is important for numerical stability when performing calculations

4. Flattening: The 2D image array is reshaped to a 2D array `pix` with the number of pixels as the number of rows and 3 columns representing the color channels. This makes it ready for processing in k-means clustering.

5. Color Definitions: A color palette is defined as a list of tuples where each tuple represents a color in normalized RGB coordinates. These are some common colors that will be used to recolor the image after clustering.

6. Initial Centroids: A dictionary `initial_centroids` is created to hold lists of initial centroid positions for the k-means algorithm. This is done for different values of `k`, indicating the number of clusters or colors the algorithm will reduce the image to.

7. K-means Clustering Algorithm: A function `k_means` is defined to perform the clustering operation. It takes as input the flattened image data `pix`, an initial set of centroids, and the number of clusters, `k`.
   - The loop inside the function iterates a maximum of 50 times or until convergence (where centroids stop changing).
   - The Euclidean distance is calculated between each pixel and each centroid, and each pixel is assigned to its nearest centroid.
   - New centroids are calculated as the mean of the pixels assigned to each centroid.
   - If centroids don't change, the loop is exited.
   - The sum of squared distances (SSE) is calculated as a measure of how tightly grouped the pixel clusters are around the centroids.

8. Running K-means for Different K: The k-means algorithm is run for `k` values of 2, 3, 6, and 10 with their corresponding initial centroids defined earlier. For each `k`, the final SSE is printed, and an image is recolored with the final centroids representing the cluster colors. The recolored image is displayed using `matplotlib`.
