---
title: "python error 16.04"
date: 2019-04-23
forum: General Help
---

### Post by rsteinmetz70112 on 2019-04-23
I'm getting the following error:

```
 File "/usr/lib/python3/dist-packages/pkg_resources/_vendor/packaging/version.py", line 10, in <module>
    from ._structures import Infinity
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 673, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 661, in exec_module
  File "<frozen importlib._bootstrap_external>", line 765, in get_code
  File "<frozen importlib._bootstrap_external>", line 476, in _compile_bytecode
ValueError: bad marshal data (invalid reference)

```

It appears to indicate something is wrong with "/usr/lib/python3/dist-packages/pkg_resources/_vendor/packaging/version.py" I've reinstalled python3
Anybody got any idea what's causing this error?

---

### Post by rsteinmetz70112 on 2019-04-23
I'm not sure how I stumbled across it but reinstalling python3-pkg-resources seems at least to have eliminated the error above.

```
# apt install --reinstall python3-pkg-resources
```

I earlier had figured out is was a python problem and began reinstalling python packages. I finally got lucky

---

