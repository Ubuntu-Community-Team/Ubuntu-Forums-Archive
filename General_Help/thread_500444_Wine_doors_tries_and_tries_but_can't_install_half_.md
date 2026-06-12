---
title: "Wine doors tries and tries but can't install half life 2"
date: 2007-07-13
forum: General Help
---

### Post by djrobthaman on 2007-07-13
Hello again,

I'm using wine doors and one of the programs in the list is half life 2.   It's pretty much a no brainer to install that one, but it won't install :(.

If I run it through the console I get the following output:

```

douglas@douglas-desktop:~$ /home/douglas/bin/wine-doors
Started logging session
Checking wine drive: /home/douglas/.wine/
Resolving dependencies for hl2 
Installing Application: hl2 version 2
Warning: Can't find executable /home/douglas/.wine/dosdevices/d:/hl2.exe, Assuming CD drive path
Traceback (most recent call last):
  File "/home/douglas/.local/share/wine-doors/src/queue.py", line 145, in Execute
    app_pack = ApplicationPack( INSTALL, pack, version, repo )
  File "/home/douglas/.local/share/wine-doors/src/application.py", line 127, in __init__
    self.InstallApplication()
  File "/home/douglas/.local/share/wine-doors/src/application.py", line 279, in InstallApplication
    self.status = wine.Execute( installer, installer_args )
  File "/home/douglas/.local/share/wine-doors/src/wine.py", line 185, in Execute
    log.Warn("Can't find executable %s, Assuming CD drive path" % executable)
  File "/home/douglas/.local/share/wine-doors/src/log.py", line 44, in Warn
    if flush: self.file.flush()
NameError: global name 'flush' is not defined

```

Does anybody know what this flush is (is that the error?)  or how I can get it to work?

Thanks

---

