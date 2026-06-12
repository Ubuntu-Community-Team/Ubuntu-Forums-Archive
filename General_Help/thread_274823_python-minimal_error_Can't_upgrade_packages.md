---
title: "python-minimal error: Can't upgrade packages"
date: 2006-10-10
forum: General Help
---

### Post by mdorn on 2006-10-10
Hi all,

I'm a long-time Ubuntu user, have been using Dapper for several months without much trouble, but I have a pretty major problem since my last package update: I can no longer upgrade any packages.  Here's my "apt-get upgrade" output:

```

Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  awstats gdb openssl python2.4-doc python2.4-examples
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B/8475kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up python2.4-minimal (2.4.3-0ubuntu6) ...
Compiling python modules in /usr/lib/python2.4 ...
Compiling /usr/lib/python2.4/site-packages/i18ndude/tests/input/test2.py ...
  File "/usr/lib/python2.4/site-packages/i18ndude/tests/input/test2.py", line 18
    {'map': zero})
SyntaxError: non-keyword arg after keyword arg

dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-minimal:
 python-minimal depends on python2.4-minimal (>= 2.4.2); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This seems to have been the result of the package updater downloading and installing the following packages:

python2.4_2.4.3-0ubuntu6_i386.deb
python2.4-dev_2.4.3-0ubuntu6_i386.deb
python2.4-gdbm_2.4.3-0ubuntu6_i386.deb
python2.4-minimal_2.4.3-0ubuntu6_i386.deb
python2.4-tk_2.4.3-0ubuntu6_i386.deb
python2.4-doc_2.4.3-0ubuntu6_all.deb
python2.4-examples_2.4.3-0ubuntu6_all.deb

I can't uninstall python-minimal, because that basically uninstalls hundreds of other packages.  Attempting to reinstall via Synaptic didn't help.

Help?

Thanks,

Matt

---

### Post by mdorn on 2006-10-11
Answering my own question:

getting rid of the /usr/lib/python2.4/site-packages/i18ndude/tests directory and re-running the upgrade seemed to do the trick.  I guess I can live without the test suite for i18ndude

---

### Post by agurk on 2006-10-15
Thanks for posting the solution, I had the same problem.

---

