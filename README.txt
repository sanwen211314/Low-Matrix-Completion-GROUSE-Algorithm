Project: Low rank matrix completion using GROUSE

Authors: 

1. Amit Kumar
2. Sophie Choe
3. Aakanksha Mathuria
	

Contents of this folder:
    Sub-folders:
        ml-latest-small: movie lens dataset
        To acknowledge use of the dataset in publications, please cite the following paper: 
            > F. Maxwell Harper and Joseph A. Konstan. 2015. The MovieLens Datasets: History and Context. ACM Transactions on Interactive Intelligent Systems (TiiS) 5, 4: 19:1�19:19. <https://doi.org/10.1145/2827872>

    Matlab Functions:
        lrmc_grouse.m: target algorithm (Low rank matrix completion using GROUSE)
        
    Matlab scripts:
        1. test_synthetic_sampprob.m: Plots the estimation error for different amount of revealed samples. Takeaway: As expected the estimation gets better as more and more samples are revealed. But the performance is extremely good even for very few revealed samples. Plot saved as synthetic_esterr_vs_sampling_probability.eps.
        
        2. test_synthetic_rank.m: Plots the estimation error as the rank of the recovery matrix is changed while the rank of the true matrix is fixed. Takeaway: as expected, the recovery error is large if the rank of the recovery matrix is lower than the rank of the true matrix. Plot saved as synthetic_esterr_vs_estimation_rank.eps.
        
        3. test_photo.m: Result of the algorithm on the same image that was used for the final class demo. The result looks quite poor. Probably because the original image was close to full rank, so a strictly low rank estimate has high error. Result saved as image_recovery_cameraman.eps.
        
        4. test_movielens.m: Runs the algorithm on movie lens dataset.
        The firsr part of the script runs the algorithm on the full dataset and plots the estimation error vs the rank of the recovered matrix. This looks great. The plot is saved as movielens_esterr_vs_estimation_rank.eps.
        
        The second part runs the algorithm on 80% of the full set (training set) anduses the remaining 20% examples (test set) to check how well the prediction based on this method would work. The prediction error starts increasing as the rank of recovered matrix exceeds 2. The plot is saved as movielens_esterr_and_predictionerr_vs_estimation_rank.eps.
        
        5. do_plots_movielens.m: The test_movielens.m script takes a long time to run. So the results are saved in this script to quickly generate the plots. It generates both of the movielens plots.
        
    MISC NOTES:
        + WE ARE USING THE LIGHT VERSION OF THE MOVIELENS DATABASE. 
        + THE MEAN IS SUBTRACTED OUT FROM RATINGS BEFORE LRMC. 
        + This algorithm doesn't have any knob for regularization. So is prone to overfitting.
        + There is no bound on how large an element of the recovered matrix can be. So, even though the ratings can only be between 0.5 and 5.0, the recoverd matrix can have entries a lot larger than this range. Before comparison with the test set, we limit the prediction to be within the valid range.
        
    Plots:
        *.eps: Plots generated by the above scripts.
        
    MAT files:
        1. cameraman.mat: The original cameraman image used for testing this algorithm with an image.
        2. movielens_20100609.mat: result of test_movielens.m script.