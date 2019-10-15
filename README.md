# PyPESQ (WIP) - fixed version for MacOS
Pypesq is a python wrapper for the PESQ score calculation C routine. It only can be used in evaluation purpose.

## INSTALL
```
# download first, extract and execute:
python setup.py install

# or you can go back and use the original version:
pip install https://github.com/vBaiCai/python-pesq/archive/master.zip
```

## About this fix

The original error message when installed on MacOS platform is like this:
```
clang: warning: libstdc++ is deprecated; move to libc++ with a minimum deployment target of OS X 10.9 [-Wdeprecated]
    ld: library not found for -lstdc++
    clang: error: linker command failed with exit code 1 (use -v to see invocation)
    error: command 'g++' failed with exit status 1
```

The problem is fixed by explicitly designate cpp library flags inside the install script. More information can be found in the reference link.


## HOW TO USE
```python
import soundfile as sf
from pypesq import pesq

ref, sr = sf.read(...)
deg, sr = sf.read(...)

score = pesq(ref, deg, sr)
print(score)
```

# NOTICE:
OWNERS of PESQ ARE:
1.	British Telecommunications plc (BT), all rights assigned to Psytechnics Limited
2.	Royal KPN NV, all rights assigned to OPTICOM GmbH

# REFERENCES:
* [ITU-T P.862](https://www.itu.int/rec/T-REC-P.862/en)
* [C_Extensions_NumPy_arrays](https://scipy-cookbook.readthedocs.io/items/C_Extensions_NumPy_arrays.html)
* [kennethreitz/setup.py](https://github.com/kennethreitz/setup.py)
* [massover/accel](https://github.com/massover/accel)

# HINT
The PESQ contain 3 types of values: `NB PESQ MOS`, `NB MOS LQO`, `WB MOS LQO`.
This package only return the `NB PESQ MOS` score, which represents the `Raw MOS` for `narrowband handset listening`.

# REFERENCE
https://github.com/pandas-dev/pandas/issues/23424
