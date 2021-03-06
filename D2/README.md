## **Using n-step SARSA to cross the Frozen Lake**

**Frozen lake involves crossing a frozen lake from Start to Goal without falling into any Holes by walking over the Frozen lake**. More information on this environment can be found [here](https://www.gymlibrary.ml/environments/toy_text/frozen_lake/ "here"). The *non-slippery version* is used in the following experiments.

<img src='https://github.com/siddarth-c/RL-Basics/blob/main/D2/Figs/2022-06-29-20-02-59.png' width='250'>
  
  gym.make('FrozenLake-v1', desc = None, map_name = "8x8", is_slippery = False)
  
------------

## Algorithm

n-step SARSA is used to find the optimal policy. The algorithm is defined as

<img src='https://github.com/siddarth-c/RL-Basics/blob/main/D2/Figs/2022-07-08-16-01-33.png' width='1000'>

Different combinations of 'n' and 'learning rate (alpha)' were tried out, namely,

$n \in {3, 5, 7}$ and $alpha \in {0.25, 0.5, 0.75}$

# Results

The following is the learnt policy for a 7-step SARSA with a learning rate of 0.75. The green line indicates the optimal path, where as the orange lines indicate the position of the holes.

<img src='https://github.com/siddarth-c/RL-Basics/blob/main/D2/Figs/PolicyLearnt.png' width='200'>

This policy takes 14 steps, the optimal number, to reach the goal. The same could be observed from the below graph.

<img src='https://github.com/siddarth-c/RL-Basics/blob/main/D2/Figs/output.png' width='1000'>

The graph is a plot between the time taken to complete an episode and the corresponding episode number. It is quite obvious that the number of time steps decreases with an increase in the episodes and gradually saturates. But it is to be noted that the policy converges quicker when the learning rate is increased.

<img src='https://github.com/siddarth-c/RL-Basics/blob/main/D2/Figs/output2.png' width='1000'>

And similar to Example 7.1, intermediate 'n' values perform better.

With the same parametes, a simple scaling of the reward by 10 gives quicker convergence. But the same did not happen when the agent was punished for every time step it takes till it reaches the goal. It chose death. Instead of reaching the goal (whose reward was now scaled upto 1000), it chose to end the episode by moving into the closest hole. Increasing the exploration epsilon till 0.9 did not work too. Maybe it requires a completely new set of parameters, or it was just too much for the agent to handle 🤷‍♂️.

<img src='https://github.com/siddarth-c/RL-Basics/blob/main/D2/Figs/output3.png' width='1000'>
