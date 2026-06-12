---
title: "Problems installing SchoolTool"
date: 2014-06-18
forum: General Help
---

### Post by kb6wij on 2014-06-18
Hello! I'm new to the forums and I'm not sure this is the correct place to post my problem. If not, please let me know!

I used Ubuntu Software Center to install SchoolTools, but the installation failed. I've attempted to uninstall it, but I get the following messages:
> Setting up python-hurry.query (1.1.0-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2372, in <module>
    main()
  File "/usr/bin/pycentral", line 2366, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1505, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing python-hurry.query (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-hurry.query
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm running Ubuntu version 12.04 LTS. Python version is 2.7.3. I'm not sure how to proceed. Any suggestions would be MOST appreciated! :D

Thanks! Joe KB6WIJ

---

