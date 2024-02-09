# Manipulator control with Reinforcement Learning

## Agent performance at different training episodes
|:----------------------------:|:----------------------------:|
|<p style="text-align: center;">5 episodes</p>|<p style="text-align: center;">50 episodes</p>|
|<img src="assets/5.gif" alt="1" width = 360px height = 360px >|<img src="assets/50.gif" alt="1" width = 360px height = 360px >|
|<p style="text-align: center;">200 episodes</p>|<p style="text-align: center;">1000 episodes</p>|
|<img src="assets/200.gif" alt="1" width = 360px height = 360px >|<img src="assets/1000.gif" alt="1" width = 360px height = 360px >|

This project focuses on controlling a 7 DOF robot arm provided in the [panda_gym](https://github.com/qgallouedec/panda-gym) reacher environment using two continuous reinforcement learning algorithms: DDPG (Deep Deterministic Policy Gradients) and TD3 (Twin Delayed Deep Deterministic Policy Gradients). The technique of Hindsight Experience Replay is used to enhance the learning process of both algorithms.

## Continuous RL Algorithms

<p align="justify">
Continuous reinforcement learning deals with environments where actions are continuous, such as the precise control of robotic arm joints or controlling the throttle of an autonomous vehicle. The primary objective is to find policies that effectively map observed states to continuous actions, ultimately optimizing the accumulation of expected rewards. Several algorithms have been specifically developed to address this challenge, including DDPG, TD3, SAC, PPO, and more.
</p>

### 1- DDPG (Deep Deterministic Policy Gradients)

<p align="justify">
DDPG is an actor-critic algorithm designed for continuous action spaces. It combines the strengths of policy gradients and Q-learning. In DDPG, an actor network learns the policy, while a critic network approximates the action-value (Q-function). The actor network directly outputs continuous actions, which are evaluted by the critic network to find the best action thus allowing for fine-grained control.
</p>

### 2- TD3 (Twin Delayed Deep Deterministic Policy Gradients)

<p align="justify">
TD3 is an enhancement of DDPG that addresses issues such as overestimation bias. It introduces the concept of "twin" critics to estimate the Q-value (it uses two critic networks instead of a single one like in DDPG), and it uses target networks with delayed updates to stabilize training. TD3 is known for its robustness and improved performance over DDPG.
</p>

## Hindsight Experience Replay

<p align="justify">
Hindsight Experience Replay (HER) is a technique developed to address the challenge of sparse and binary rewards in RL environments. For example, in many robotic tasks, achieving the desired goal is rare, and traditional RL algorithms struggle to learn from such feedback (agent always gets a zero reward unless the robot successfully completed the task which makes it difficult for the algorithm to learn as it doesn't know if the steps done were good or not).
</p>

<p align="justify">
HER tackles this issue by reusing past experiences for learning, even if they didn't lead to the desired goal. It works by relabeling and storing experiences in a replay buffer, allowing the agent to learn from both successful and failed attempts which significantly accelerates the learning process.
</p>

- You can train a given model simply by running one of the files in the `training` folder.

- You can change the values of the hyperparameters of both algorithms (learning_rate (alpha/beta), discount factor (gamma),...) by going directly to each agent class in the `agents` folder. The architecture of the Actor/Critic networks can be modified from the `networks.py` file.

Link to HER paper: https://arxiv.org/pdf/1707.01495.pdf
