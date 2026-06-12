---
title: "dput Error"
date: 2015-09-03
forum: General Help
---

### Post by mkykadir-96 on 2015-09-03
Hello there, I have **Ubuntu 14.04** installed and I wanted to the set up a build environment for Android Source. But Python things messed up everything. I downloaded Python 2.6 tar-ball from official web-site and manually builded and installed the system. It changed the default Python version of the system to 2.6. It has got problems with importing ssl but Python 2.7, which came with system, doesn't have. I decided to remove Python 2.6, I deleted files by hand. In terminal when I type "python --version" it was giving me "Python 2.6.9". So I added a line to "~/.bashrc", which was "alias python=python2.7". So now when I type "python --version" to terminal, it gives "Python 2.7.6", but I have problems with "dput". When I try to build the source of Android it gives me error about python imports as "apt-get upgrade" does. 

```

//checks packages asks for Y/n

Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named compileall
dpkg: error processing package dput (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 dput
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now can I fix this or I just need the reinstall the Ubuntu. But I don't want to download Android source agan. :)
**NOTE 1: **"dput" gives an error every boot-up before desktop comes up to screen as a "System error send report". I am sending reports
**NOTE 2:  **ERROR OF ANDROID SOURCE CODE BUILD
```

Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "build/tools/findleaves.py", line 23, in <module>
    import os
ImportError: No module named os
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "build/tools/findleaves.py", line 23, in <module>
    import os
ImportError: No module named os
*** Error in `make': free(): invalid next size (fast): 0x000000000240b760 ***
Aborted (core dumped)

```

---

### Post by dino99 on 2015-09-03
i suppose the problem is due to the removal of python2.6: deleting files is not enough (and should not be done) as each app/package installation create/write many settings here & there (following the OS needs). So to cleanly remove python2.6, you should have used the package manager to do a 'complete removal, aka purging); and creating an alias is really a dirty idea.
That said, reinstall python2.6, to then purging it; that should stop the system being disturbed

---

### Post by mkykadir-96 on 2015-09-03
> **dino99 said:**
> i suppose the problem is due to the removal of python2.6: deleting files is not enough (and should not be done) as each app/package installation create/write many settings here & there (following the OS needs). So to cleanly remove python2.6, you should have used the package manager to do a 'complete removal, aka purging); and creating an alias is really a dirty idea.
That said, reinstall python2.6, to then purging it; that should stop the system being disturbed

Thanks for answer, I read a topic in this forums yesterday, it was saying; default Python sources do not have uninstall methods. I downloaded source tarball, built it from source by following instructions inside README file of archive. I can reinstall it but how can I remove it? I am a newbiw of Android Source tree and linux... I was sleeping with Windows' .exes :D

---

### Post by mkykadir-96 on 2015-09-03
I reinstalled the Python-2.6.9 to the system and "dput" does not give error anymore. I will reinstall the ubuntu. I am copying AOSP source files and I hope "repo sync" can handle that.

---

