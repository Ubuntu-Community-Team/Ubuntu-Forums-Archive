---
title: "numarray 1.3.1?"
date: 2005-06-29
forum: General Help
---

### Post by jtan325 on 2005-06-29
Hi,

I need numarray 1.3.1 for work, but synaptic doesn't seem to find it in its repositories, and i am stuck wtih 1.1.3, which looks like some ubuntu-specific version. 

any ideas? tried downloading the source, unpacking it, and then 

"sudo python setup.py install --gencode" 

as it says to do a default install in the installation instructions, but then as it's installing, it complains about 

copying Examples/convolve/__init__.py -> build/lib.linux-i686-2.4/numarray/examples/convolve
copying Examples/convolve/benchmark.py -> build/lib.linux-i686-2.4/numarray/examples/convolve
copying Examples/convolve/dtest.py -> build/lib.linux-i686-2.4/numarray/examples/convolve
copying Examples/convolve/lineshape.py -> build/lib.linux-i686-2.4/numarray/examples/convolve
running build_ext
Traceback (most recent call last):
  File "setup.py", line 222, in ?
    main()
  File "setup.py", line 213, in main
    setup(**p)
  File "/usr/lib/python2.4/distutils/core.py", line 149, in setup
    dist.run_commands()
  File "/usr/lib/python2.4/distutils/dist.py", line 946, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/distutils/command/install.py", line 506, in run
    self.run_command('build')
  File "/usr/lib/python2.4/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/distutils/command/build.py", line 112, in run
    self.run_command(cmd_name)
  File "/usr/lib/python2.4/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/distutils/command/build_ext.py", line 254, in run
    customize_compiler(self.compiler)
  File "/usr/lib/python2.4/distutils/sysconfig.py", line 161, in customize_compiler
    cpp = cc + " -E"           # not always
TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'

anyone have any ideas? thanks

---

