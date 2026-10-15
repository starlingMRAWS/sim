# PySocialForce Simulation Environment 

This repository contains setup instructions and evaluation code for running pedestrian crowd simulations using `PySocialForce`and `Pygame`

## 1. Prerequisites & Environment Setup

### Step 1.1: Install Miniconda
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh
bash ~/miniconda.sh -b -u -p ~/miniconda3
~/miniconda3/bin/conda init bash
rm ~/miniconda.sh
source ~/.bashrc
```

### Step 1.2: Create and Activate Virtual Environment
```bash
conda create -n swarm_env python=3.10 -y
conda activate swarm_env
```

## 2. Package Installation

Install all required dependencies in a single command:
```bash
pip install numpy scipy numba pygame pettingzoo pysocialforce imageio imageio-ffmpeg opencv-python pandas matplotlib gdown
```

> **Note for WSL Users:** To view Pygame GUI visualization windows natively in Windows Subsystem for Linux (WSL), use **WSLg** (Windows Subsystem for Linux GUI), which comes built into Windows 11 and recent releases of Windows 10. WSLg handles X11 and Wayland graphics automatically without requiring manual X-server setup or exporting `DISPLAY` variables.

## 3. Testing on Real Pedestrian Datasets (ETH/UCY)

To evaluate PySocialForce against real pedestrian crowd data, download the standard ETH/UCY benchmark datasets (e.g., ETH, HOTEL, ZARA01, ZARA02, UNIV).

### Step 3.1: Download Benchmark Datasets to Local Machine
You can clone or download the standardized raw trajectory files directly into your project directory using `git` or `curl`:

```bash
# Create dataset directory
mkdir -p datasets/eth_ucy
cd datasets/eth_ucy

# Download ETH/UCY trajectory files from open benchmark repositories
curl -O https://raw.githubusercontent.com/agrimgupta2602/sgan/master/datasets/eth/univ/pixel_pos/student03.txt
curl -O https://raw.githubusercontent.com/agrimgupta2602/sgan/master/datasets/ucy/zara/zara01/obs_mat.txt

cd ../..
```

### Step 3.2: Run Evaluation Script on Dataset (`test_dataset.py`)

Create `test_dataset.py` to parse the real-world trajectories and simulate the agent movements using `PySocialForce`:

Run dataset evaluation:
```bash
python test_dataset.py
```

## 4. Testing on Synthetic Datasets

You can generate custom synthetic crowd scenarios (such as cross-flows, bidirectional bottlenecks, or circular squeezes) to test social force interactions under controlled conditions.

### Run Synthetic Benchmark (`synthetic_test.py`)

Create `synthetic_test.py`:

Run synthetic benchmark:
```bash
python synthetic_test.py
```
