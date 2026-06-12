---
title: "Can't install idlefork"
date: 2005-08-20
forum: General Help
---

### Post by Guest1234 on 2005-08-20
I have downloaded IDLEFork-0.9b1, and I'm trying to install it.

after I extracted IDLEfork-0.9b1.tar.gz to directory IDLEfork-0.9b1, I read that
in the INSTALL.txt all I have to do to install it is to type:
"python setup.py install"

but when I do I get these error messages:
```
running install
Traceback (most recent call last):
  File "setup.py", line 117, in ?
    scripts = [os.path.join(pkg_dir, idle_name)]
  File "/usr/lib/python2.2/distutils/core.py", line 138, in setup
    dist.run_commands()
  File "/usr/lib/python2.2/distutils/dist.py", line 902, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.2/distutils/dist.py", line 921, in run_command
    cmd_obj.ensure_finalized()
  File "/usr/lib/python2.2/distutils/cmd.py", line 112, in ensure_finalized
    self.finalize_options()
  File "/usr/lib/python2.2/distutils/command/install.py", line 267, in finalize_options
    (prefix, exec_prefix) = get_config_vars('prefix', 'exec_prefix')
  File "/usr/lib/python2.2/distutils/sysconfig.py", line 417, in get_config_vars
    func()
  File "/usr/lib/python2.2/distutils/sysconfig.py", line 322, in _init_posix
    raise DistutilsPlatformError(my_msg)
distutils.errors.DistutilsPlatformError: invalid Python installation: unable to open /usr/lib/python2.2/config/Makefile (No such file or directory)
``` 

I have python2.2 installed, and I checked and the directory
"/usr/lib/python2.2/config" is empty, and doesn't have a file "Makefile", but how
am I supposed to create this file?

And is this the only problem or is there something else?

---

### Post by wheelscribe on 2005-10-09
[QUOTE=Guest1234]I have downloaded IDLEFork-0.9b1, and I'm trying to install it.

after I extracted IDLEfork-0.9b1.tar.gz to directory IDLEfork-0.9b1, I read that
in the INSTALL.txt all I have to do to install it is to type:
"python setup.py install"

but when I do I get these error messages:
```
running install
Traceback (most recent call last):
  File "setup.py", line 117, in ?
    scripts = [os.path.join(pkg_dir, idle_name)]
  File "/usr/lib/python2.2/distutils/core.py", line 138, in setup
    dist.run_commands()
  File "/usr/lib/python2.2/distutils/dist.py", line 902, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.2/distutils/dist.py", line 921, in run_command
    cmd_obj.ensure_finalized()
  File "/usr/lib/python2.2/distutils/cmd.py", line 112, in ensure_finalized
    self.finalize_options()
  File "/usr/lib/python2.2/distutils/command/install.py", line 267, in finalize_options
    (prefix, exec_prefix) = get_config_vars('prefix', 'exec_prefix')
  File "/usr/lib/python2.2/distutils/sysconfig.py", line 417, in get_config_vars
    func()
  File "/usr/lib/python2.2/distutils/sysconfig.py", line 322, in _init_posix
    raise DistutilsPlatformError(my_msg)
distutils.errors.DistutilsPlatformError: invalid Python installation: unable to open /usr/lib/python2.2/config/Makefile (No such file or directory)
``` 

I have python2.2 installed, and I checked and the directory
"/usr/lib/python2.2/config" is empty, and doesn't have a file "Makefile", but how
am I supposed to create this file?

And is this the only problem or is there something else?[/QUOTE]


I'm having the same problem under Python 2.4. Any clues are much appreciated.

Thanks,
Ben

---

### Post by joebwan on 2005-10-11
I think if you execute a 

"sudo apt-get install python-dev"

you should be able to get this to work.  I had the same problem with another package complaining about Makefile not being in the config directory.

---

