# Robot-Reach-RL

Reinforcement learning agents for robotic reaching tasks using DDPG and PPO with Hindsight Experience Replay (HER) on the Panda robot environment.

## Overview

This project trains RL agents to solve the `PandaReach-v2` task from `panda-gym`, where a Franka Panda robot arm must reach a target position in 3D space. Two algorithms are implemented:

- **DDPG** (Deep Deterministic Policy Gradient) with HER replay buffer and Gaussian action noise
- **PPO** (Proximal Policy Optimization) with custom network architecture

Both agents use a 3-layer MLP policy (512-512-512) and include a custom callback for saving the best model based on rolling mean reward.

## Algorithms

| | DDPG | PPO |
|---|---|---|
| Policy | MultiInputPolicy | MultiInputPolicy |
| Network | 512 × 512 × 512 | 512 × 512 × 512 |
| Replay Buffer | HER (future, k=4) | — |
| Action Noise | Gaussian (σ=0.1) | — |
| Batch Size | 2048 | 2048 |
| Gamma | 0.95 | 0.95 |
| Learning Rate | 1e-3 | 1e-3 |
| Training Steps | 1M | 1M |

## Tech Stack

`Python` · `Stable-Baselines3` · `OpenAI Gym` · `panda-gym` · `PyBullet` · `NumPy`

## Getting Started

```bash
git clone https://github.com/pathal-r/Robot-Reach-RL.git
cd Robot-Reach-RL
pip install stable-baselines3 panda-gym gym numpy matplotlib
```

### Train DDPG

```bash
python Agents/DDPG.py
```

### Train PPO

```bash
python Agents/PPO.py
```

Best models are saved to `tmp/best_model` during training. Training progress is plotted after completion.

## Project Structure

```
Robot-Reach-RL/
└── Agents/
    ├── DDPG.py    # DDPG agent with HER
    └── PPO.py     # PPO agent
```
