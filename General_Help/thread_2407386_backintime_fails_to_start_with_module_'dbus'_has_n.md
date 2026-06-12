---
title: "backintime fails to start with module 'dbus' has no attribute 'SystemBus' error"
date: 2018-12-03
forum: General Help
---

### Post by average6502 on 2018-12-03
$ backintime
    
    Back In Time
    Version: 1.1.24
    
    Back In Time comes with ABSOLUTELY NO WARRANTY.
    This is free software, and you are welcome to redistribute it
    under certain conditions; type `backintime --license' for details.
    
    Traceback (most recent call last):
      File "/usr/share/backintime/common/tools.py", line 1212, in __init__
        bus = dbus.SystemBus()
    AttributeError: module 'dbus' has no attribute 'SystemBus'
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/usr/share/backintime/common/backintime.py", line 874, in <module>
        start_app()
      File "/usr/share/backintime/common/backintime.py", line 463, in start_app
        return getConfig(args, False)
      File "/usr/share/backintime/common/backintime.py", line 584, in getConfig
        cfg = config.Config(args.config)
      File "/usr/share/backintime/common/config.py", line 272, in __init__
        self.setupUdev = tools.SetupUdev()
      File "/usr/share/backintime/common/tools.py", line 1215, in __init__
        except dbus.exceptions.DBusException as e:
    AttributeError: module 'dbus' has no attribute 'exceptions'




I've tried purging and reinstalling, and installing from source. Same errors. 


I also use conda, but I removed that from the path temporarily. If I have that in my path, then I get a ModuleNotFoundErrro:No module named 'dbus'. 


This used to work just fine. I don't know why it's failing now. 




[FONT=monospace]print(dbus.__file__) yields [/FONT][FONT=monospace]/usr/local/lib/python3.5/dist-packages/dbus/__init__.py

which matches the version of python I'm using. [/FONT][FONT=verdana]print(sys.version) in backintim.py yields [/FONT][FONT=verdana]3.5.2.

I don't know why this isn't working. Any thoughts? [/FONT]

---

### Post by thomi_ch on 2018-12-10
Hey

i'm getting same error...
check this, i opened a issue.. maybe they can help, solve it..
[https://github.com/bit-team/backintime/issues/963](https://github.com/bit-team/backintime/issues/963)

thomi

---

