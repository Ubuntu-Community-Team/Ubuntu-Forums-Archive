---
title: "get_python_lib() returns path to python3 instead of python3.6"
date: 2019-02-04
forum: General Help
---

### Post by stellarspot on 2019-02-04
Python version is Python 3.6.7 (default, Oct 22 2018, 11:32:17)
Ubuntu 18.04.01

When I call get_python_lib() function to get the Python lib path to install my module it returns '/usr/lib/python3/dist-packages' instead of python3.6 dir:
python3 -c "from distutils.sysconfig import *;print(get_python_lib())"

This is because the source code '/usr/lib/python3.6/distutils/sysconfig.py'  has the branch on Ubuntu:

```

    if os.name == "posix":
        libpython = os.path.join(prefix,
                                 "lib", "python" + get_python_version())
        if standard_lib:
            return libpython
        elif (is_default_prefix and
              'PYTHONUSERBASE' not in os.environ and
              'VIRTUAL_ENV' not in os.environ and
              'real_prefix' not in sys.__dict__ and
              sys.prefix == sys.base_prefix):
            return os.path.join(prefix, "lib", "python3", "dist-packages")

```

However, this code does not present in the original cpython code 3.6.7:
[https://github.com/python/cpython/blob/ca7d2933a388677cc3bbc621913b479452c0f25a/Lib/distutils/sysconfig.py#L109](https://github.com/python/cpython/blob/ca7d2933a388677cc3bbc621913b479452c0f25a/Lib/distutils/sysconfig.py#L109)

Is it the right behavior?

Why the get_python_lib() result should depend on PYTHONUSERBASE and VIRTUAL_ENV and points to python3 instead of python3.6?

---

### Post by Skaperen on 2019-02-04
the first number of the version, the major version, 2 or 3 these days, is supposed to be the compatibility level.  that it, if something needs something that came along in some 3.x.x version, then a reference to 3 to get access to the latest 3.z.z should work.  it might even work when confined to a like system.  in reality, some things do break as the minor version goes up, and your script might find itself on an unlike system with an earlier 3.w.w system that doesn't have that new thing from 3.x.x.  but it is common practice in many cases to just use the major number or in many other cases to use major.minor.  you apparently need the latter.

things like this are why containers are getting popular.

---

### Post by stellarspot on 2019-02-04
I need the major.minor version and it is what the the get_python_lib() returns according to the code from the official [https://github.com/python/cpython](https://github.com/python/cpython) repository.
The question is why the Python 3 sources are different on Ubuntu?
Where are sources for Python 3 are got from on Ubuntu?

Is it a right behavior that  get_python_lib() returns python3 dir when 'PYTHONUSERBASE' not in os.environ and 'VIRTUAL_ENV' not in os.environ and python3.6 otherwise?

---

