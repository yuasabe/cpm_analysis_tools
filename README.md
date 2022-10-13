# CPM Analysis Tools

Dissecting CPMs from tcpdumps using Python for CPM analysis.

## Prerequisites

- Wireshark (3.6.7 or above)
- Python3

## Quickstart

### 1. Create Python environment.

```
# Create Virtual Environment
$ python -m venv venv

# Activate Virtual Environment
$ . venv/bin/activate

# Install Python Packages
$ pip install -r requirements.txt
```

### 2. Fix bug

Currently, there is a bug when using Jupyter notebooks and Pyshark. However, there is an easy fix.
https://github.com/KimiNewt/pyshark/issues/360#issuecomment-700425352

First, run the Python command line and find the path for the module `tornado`.
In the case below, the required path is `/home/yuasabe/Developer/cpm_analysis_tools/venv/lib/python3.8/site-packages/tornado/__init__.py`.
```
$ python
>>> import tornado
>>> print(tornado)
<module 'tornado' from '/home/yuasabe/Developer/cpm_analysis_tools/venv/lib/python3.8/site-packages/tornado/__init__.py'>
```

Open the file in the path you just found (in this case: `/home/yuasabe/Developer/cpm_analysis_tools/venv/lib/python3.8/site-packages/tornado/__init__.py`), and add the following lines to the end of the file.

```
...
import nest_asyncio
nest_asyncio.apply()
```

Save.

### 3. Launch Jupyter Lab.

```

# Launch Jupyter Lab (This will open a browser)
$ jupyter lab

```