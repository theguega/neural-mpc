# neural-mpc

Accepted as a poster at the IEEE ICRA 2026 Workshop on RL in the Era of IL: this work replaces the IK + MPC control stack with a neural network surrogate policy.

Paper (PDF): [https://theguega.github.io/neural-mpc/main.pdf](https://theguega.github.io/neural-mpc/main.pdf)  
Poster (HTML): [https://theguega.github.io/neural-mpc/poster.html](https://theguega.github.io/neural-mpc/poster.html)

[![Python Version](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

A project for approximating Model Predictive Control (MPC) policies using neural networks for a 3-degree-of-freedom (3DOF) robot arm simulation in MuJoCo.

## Overview

This repository implements a surrogate modeling approach to replace computationally expensive MPC controllers with fast neural network approximations. The project focuses on trajectory optimization and control for robotic manipulation tasks, enabling real-time performance while maintaining control accuracy.

## Features

- **MuJoCo Simulation**: Realistic physics simulation of a 3DOF robot arm
- **Neural Network Surrogates**: Trainable NN models to approximate IK + MPC policies
- **Data Generation**: Scripts for collecting MPC trajectory data
- **Evaluation Tools**: Closed-loop testing and performance comparison
- **Visualization**: Comprehensive plotting and analysis tools

## Installation

### Prerequisites

- Python 3.12+

### Setup

1. Clone the repository:

   ```bash
   git clone git@github.com:theguega/neural-mpc.git
   cd neural-mpc
   ```

2. Install dependencies using uv:

   ```bash
   uv sync
   ```

## Usage

### Data Generation

Solve the IK + MPC trajectory data for training:

```bash
uv run python scripts/data_generator.py
```

### Training

Train neural network surrogates using the provided Jupyter notebook:

```bash
jupyter notebook scripts/neural-mpc-training.ipynb
```

### Interactive Simulation

Launch the MuJoCo interactive viewer:

```bash
uv run python scripts/interactive_mujoco_launcher.py
```

### Closed-Loop Testing

Evaluate controller performance:

```bash
uv run python scripts/closed_loop_eval.py
```

### Dataset Analysis

Analyze closed-loop evaluation results and generate comparison plots:

```bash
uv run python scripts/analyze_closed_loop.py
```

### Visualization

Visualize scikit-learn baseline results:

```bash
uv run python scripts/visualize_scikit_results.py
```

### Dataset Scaling

Test model performance with different dataset sizes:

```bash
uv run python scripts/dataset_scale.py
```

### Dataset Replay

Replay dataset trajectories in MuJoCo for visualization:

```bash
uv run python scripts/replay_dataset_mujoco.py
```

## Project Structure

```
├── docs/                    # Research report, figures, and documentation
├── models/                  # MuJoCo model files
├── prek.toml                # Prek hook configuration
├── pyproject.toml           # Project metadata and dependencies
├── scripts/                 # Utility scripts and notebooks
│   ├── analyze_closed_loop.py       # Closed-loop performance analysis
│   ├── closed_loop_eval.py          # Closed-loop evaluation
│   ├── data_generator.py            # MPC data generation
│   ├── dataset_scale.py             # Dataset scaling experiments
│   ├── interactive_mujoco_launcher.py # Interactive MuJoCo viewer
│   ├── neural-mpc-training.ipynb     # Main training notebook
│   ├── replay_dataset_mujoco.py     # Dataset visualization
│   ├── scikit_learn_baseline.py     # Baseline model training
│   └── visualize_scikit_results.py  # Results visualization
├── src/neural_mpc/          # Core package
│   ├── mpc_controller.py    # MPC implementation
│   ├── mujoco_env.py        # MuJoCo environment wrapper
│   └── utils.py             # Helper functions
├── tests/                   # Unit tests
└── uv.lock                  # Locked dependency resolution
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Theo - [GitHub](https://github.com/theguega)
Dexter - [GitHub](https://github.com/dexterteo4)

## Citation

If you use this code in your research, please cite the relevant papers from the `docs/refs.bib` file or refer to this repository:

```bibtex
@misc{neural-mpc,
  title={Behavior Cloning of MPC for 3-DOF Robotic Manipulators},
  author={Theo Guegan, Wen Jie Dexter Teo},
  year={2025},
  url={https://github.com/theguega/neural-mpc}
}
```
