---
title: "cedega problem with GTA San Andreas"
date: 2008-01-16
forum: General Help
---

### Post by hirou on 2008-01-16
I just installed cedega and used cedega to install GTA: San Andreas. Install went fine. Then when I try to run the game using the cedega command I get ```
root@hirou-desktop:/home/hirou/.cedega/Dot TransGaming/c_drive/Program Files/Rockstar Games/GTA San Andreas# cedega gta_sa.exe/usr/lib/transgaming_cedega/gddb.py:19: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2379, in <module>
    Point2Play_ref = Point2Play.Point2Play( config_file )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 352, in __init__
    config_file.readfp( file( filename, "r" ) )
IOError: [Errno 2] No such file or directory: '/root/.cedegarc'
root@hirou-desktop:/home/hirou/.cedega/Dot TransGaming/c_drive/Program Files/Rockstar Games/GTA San Andreas# 

```

As I am a complete noob I have no idea what this means, no one else seems to have had this problem.

---

### Post by DoktorSeven on 2008-01-16
You're trying to run it as root.  Go back to your normal user and run it.

---

### Post by hirou on 2008-01-16
thankyou for reply
I try as normal user and get the following: 
```
hirou@hirou-desktop:~/.cedega/Dot TransGaming/c_drive/Program Files/Rockstar Games/GTA San Andreas$ cedega gta_sa.exe
/usr/lib/transgaming_cedega/gddb.py:19: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2471, in <module>
    retval = Point2Play_ref.winex( 1, installcmd_gamename, installcmd_exename, None, Point2Play_ref.gamedir + installcmd_gamename + "/" + "games.ini.new", Point2Play_ref.default_winex, ( dos_cwd_path, use_big_exe, pthreads_value ), cmdlineoverride=runcmd_cmdlinearg, ModifiedInstallConfigs="install_config", debug_channel=debug_channels, OverrideGameProfile=config_file_to_use, MonitorCdromEject=monitor_cdrom_eject, gddb_file=gddb_file )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 1214, in winex
    os.unlink ( path + "config" )
OSError: [Errno 13] Permission denied: '/home/hirou/.cedega/Dot TransGaming/config'
hirou@hirou-desktop:~/.cedega/Dot TransGaming/c_drive/Program Files/Rockstar Games/GTA San Andreas$ 

```

Have I installed something wrong?

---

