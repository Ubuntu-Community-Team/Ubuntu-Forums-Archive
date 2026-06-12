---
title: "Python Bad Magic Number"
date: 2014-08-01
forum: General Help
---

### Post by runasianrun on 2014-08-01
Hi Guys,

I've been using Ubuntu 13.10 on my XPS13 ultrabook for a while now and have loved every minute of it. I'm having, what looks to be a python conflict where many different system commands are failing (apt-add-repository, lsb_release etc..)

It seems as if the wrong version of python is being invoked when I run these commands, but I'm not certain and have even less of an idea on how to solve it. 

I've attached the command line prompt for both "sudo apt-add-repository ppa:kicad/ppa" and "lsb_release -a". The only commonality between the two is the following line "ImportError: bad magic number in 'apt': b'\x03\xf3\r\n'

Any ideas or help at all would be appreciated!:)

Thanks,
Brian

```
brian@TLB-XPS-L321X:~/Projects/atmega/ST7565-Parallel$ lsb_release -a
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 28, in <module>
    import lsb_release
ImportError: bad magic number in 'lsb_release': b'\x03\xf3\r\n'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
ImportError: bad magic number in 'apt': b'\x03\xf3\r\n'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 28, in <module>
    import lsb_release
ImportError: bad magic number in 'lsb_release': b'\x03\xf3\r\n'

```

```

brian@TLB-XPS-L321X:~/Projects/atmega/ST7565-Parallel$ lsb_release -a
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 28, in <module>
    import lsb_release
ImportError: bad magic number in 'lsb_release': b'\x03\xf3\r\n'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
ImportError: bad magic number in 'apt': b'\x03\xf3\r\n'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 28, in <module>
    import lsb_release
ImportError: bad magic number in 'lsb_release': b'\x03\xf3\r\n'


```

---

### Post by buntu_hugenewbie11 on 2014-08-13
I have a similar problem.
Did you ever get this working?

---

