# Description of the comma separated values (CSV) files

The Markov Chain Monte Carlo (MCMC) trace for each model has been exported as a single CSV file. For each model described in the paper, four MCMC chains were used and 5000 samples were drawn from the posterior distribution for each chain (1000 were used for tuning the sampler and then discarded, and 1000 were discarded as burn-in) with the No-U-Turn Sampler (NUTS). Thus, each CSV file contains (3000*4=) 12000 samples.

Each column in the CSV file represents a parameter of the model. Specifically:
 - `trace_off_path_glances.csv` contains the samples from the model `y ~ logN(mu, sigma_*)` with `mu = beta_* + gamma_*__#` (where `*` can be either `manual` or `acclka` and `#` is the driver ID).
 - `trace_on_path_glances.csv` contains the samples from the model `y ~ IG(mu, lambda_*)` with `mu = 3*logistic(beta_* + gamma_*__#)` (where `*` can be either `manual` or `acclka` and `#` is the driver ID).
  - `trace_percent_road_center_PRC.csv` contains the samples from the model `y ~ B(mu*phi_*, (1-mu)*phi_*)` with `mu = logistic(beta_* + gamma_*__#)` (where `*` can be either `manual` or `acclka` and `#` is the driver ID).
   - `trace_total_task_time_TTT.csv` contains the samples from the model `y ~ logN(mu, sigma_*)` with `mu = beta_* + gamma_*__#` (where `*` can be either `manual` or `acclka` and `#` is the driver ID).

Please, refer to the full paper for the details on the implementation.