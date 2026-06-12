---
title: "Installed RPM package into ubuntu problem"
date: 2019-07-09
forum: General Help
---

### Post by pedro-fox on 2019-07-09
Hi.

I accidentally installed a package using directly RPM in my ubuntu system. The package was libiconv-1.15:

```
> rpm -i libiconv-1.15-1.el6.src.rpm


rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
warning: libiconv-1.15-1.el6.src.rpm: Header V4 RSA/SHA1 Signature, key ID 87e360b8: NOKEY
warning: user repoman does not exist - using root
warning: group repoman does not exist - using root
warning: user repoman does not exist - using root
warning: group repoman does not exist - using root
warning: user repoman does not exist - using root
warning: group repoman does not exist - using root
warning: user repoman does not exist - using root
warning: group repoman does not exist - using root
```


This made damage to the machine I was working on, since 'conda install' is not working:

```
> conda install -c conda-forge r-mvoutlier 

Traceback (most recent call last):
  File "/path/to/bin/conda", line 13, in <module>
    sys.exit(main())
  File "/path/to/anaconda2/lib/python2.7/site-packages/conda/cli/main.py", line 150, in main
    return conda_exception_handler(_main, *args, **kwargs)
  File "/path/to/anaconda2/lib/python2.7/site-packages/conda/exceptions.py", line 1335, in conda_exception_handler
    return_value = exception_handler(func, *args, **kwargs)
  File "/path/to/anaconda2/lib/python2.7/site-packages/conda/exceptions.py", line 1046, in __call__
    return self.handle_exception(exc_val, exc_tb)
  File "/path/to/anaconda2/lib/python2.7/site-packages/conda/exceptions.py", line 1090, in handle_exception
    return self.handle_unexpected_exception(exc_val, exc_tb)
  File "/path/to/anaconda2/lib/python2.7/site-packages/conda/exceptions.py", line 1101, in handle_unexpected_exception
    self.print_unexpected_error_report(error_report)
  File "/home/AD/praposo/anaconda2/lib/python2.7/site-packages/conda/exceptions.py", line 1171, in print_unexpected_error_report
    from .cli.main_info import get_env_vars_str, get_main_info_str
  File "/path/to/anaconda2/lib/python2.7/site-packages/conda/cli/main_info.py", line 19, in <module>
    from ..core.index import _supplement_index_with_system
  File "/path/to/anaconda2/lib/python2.7/site-packages/conda/core/index.py", line 9, in <module>
    from .package_cache_data import PackageCacheData
  File "/path/to/anaconda2/lib/python2.7/site-packages/conda/core/package_cache_data.py", line 15, in <module>
    from conda_package_handling.api import InvalidArchiveError
ImportError: No module named conda_package_handling.api
```

I cannot detect the installed package using 'rpm -qa'.

Does anybody know why this is happening and how can I solve it?
Thank you very much in advance.

---

### Post by TheFu on 2019-07-11
First, Ubuntu doesn't use rpm nor does it use .rpm packages.
> rpm: However assuming you know what you are doing...
Did you try to remove the package?

---

