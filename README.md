import numpy as np
import matplotlib.pyplot as plt

# Parameters
r = 0.2       # Growth rate
K = 1000      # Carrying capacity (max population size)
N0 = 10       # Initial population size
time = np.linspace(0, 50, 100)  # Time points

# Logistic growth equation: dN/dt = r * N * (1 - N/K)
def logistic_growth(t, N):
    return r * N * (1 - N/K)

# Numerical solution using Euler's method
N = np.zeros(len(time))
N[0] = N0
dt = time[1] - time[0]

for i in range(1, len(time)):
    N[i] = N[i-1] + logistic_growth(time[i-1], N[i-1]) * dt

# Plot the results
plt.plot(time, N, label="Population Size")
plt.axhline(y=K, color='r', linestyle='--', label="Carrying Capacity")
plt.xlabel("Time")
plt.ylabel("Population")
plt.title("Logistic Growth Model")
plt.legend()
plt.show()
