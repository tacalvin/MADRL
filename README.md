# MADRL

This package provides implementations of the following multi-agent reinforcement learning environemnts:

- [Pursuit Evastion](https://github.com/sisl/MADRL/blob/master/madrl_environments/pursuit/pursuit_evade.py)
- [Waterworld](https://github.com/sisl/MADRL/blob/master/madrl_environments/pursuit/waterworld.py)
- [Multi-Agent Walker](https://github.com/sisl/MADRL/blob/master/madrl_environments/walker/multi_walker.py)
- [Multi-Ant](https://github.com/sisl/MADRL/blob/master/madrl_environments/mujoco/ant/multi_ant.py)

## Requirements

This package requires both [OpenAI Gym](https://github.com/openai/gym) and a forked version of [rllab](https://github.com/rejuvyesh/rllab/tree/multiagent) (the multiagent branch). There are a number of other requirements which can be found
in `rllab/environment.yml` file if using `anaconda` distribution.

## Setup

The easiest way to install MADRL and its dependencies is to perform a recursive clone of this repository.
```bash
git clone --recursive https://github.com/tacalvin/MADRL/
```

Then, add directories to `PYTHONPATH`
```bash
export PYTHONPATH=$(pwd):$(pwd)/rltools:$(pwd)/rllab:$PYTHONPATH
```

Install the required dependencies. Good idea is to look into `rllab/environment.yml` file if using `anaconda` distribution.

`conda env create -f rllab/enviroment.yml`
(Note remove the mocojo-py line from `rllab/enviroment.yml` before creating the enviroment)

`source activate rllab3`
After that move into mocojo-py and run `python setup.py install`

## Usage

Example run with curriculum:

```bash
python3 runners/run_multiwalker.py rllab \ # Use rllab for training
    --control decentralized \ # Decentralized training protocol
    --policy_hidden 100,50,25 \ # Set MLP policy hidden layer sizes
    --n_iter 200 \ # Number of iterations
    --n_walkers 2 \ # Starting number of walkers
    --batch_size 24000 \ # Number of rollout waypoints
    --curriculum lessons/multiwalker/env.yaml
```

## Details

Policy definitions exist in `rllab/sandbox/rocky/tf/policies`.
