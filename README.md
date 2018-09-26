# box-cox-transformation

from scipy import stats
import pandas as pd
import numpy as np
import pylab 
import matplotlib.pyplot as plt

%matplotlib inline

# Creat dummy arrays, skewed to the left
x = stats.loggamma.rvs(5, size=500) + 5

# How is the distribution for x?
pd.Series(x).hist()
plt.show()
stats.probplot(x, dist="norm", plot=pylab)
pylab.show()

# What happens when log transformation?
pd.Series(np.log(x)).hist()
plt.show()
stats.probplot(np.log(x), dist="norm", plot=pylab)
pylab.show()

# What happens when sqrt transformation?
pd.Series(np.sqrt(x)).hist()
plt.show()
stats.probplot(np.sqrt(x), dist="norm", plot=pylab)
pylab.show()

# Now what happens when box-cox transformation?
x_bc, lmda = stats.boxcox(x)
pd.Series(x_bc).hist()
plt.show()
stats.probplot(x_bc, dist="norm", plot=pylab)
pylab.show()
print "lambda parameter for Box-Cox Transformation is {}".format(lmda)
