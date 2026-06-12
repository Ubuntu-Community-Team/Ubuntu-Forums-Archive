---
title: "beagle and opening files from best (gthumb/acroread and firefox)"
date: 2005-06-26
forum: General Help
---

### Post by burlap on 2005-06-26
Some apps assigned to mime types do not work with best. I have pdf assigned to acroread, jpg to gthumb and html (files, not links) to mozilla-firefox. They do not open files from best (output below). When I change system-wide settings to evince, eog and epiphany it all works. 

Sample best output:

Acroread:```
Open URI: action:_tile_24!Open
Cmd: '/usr/local/Adobe/Acrobat7.0/bin/acroread'
Arg:  /home/burlap/dokumenty/praca/wlasnoscintelektualna/swpat.pdf
Error in OpenFromMime: System.ComponentModel.Win32Exception: Cannot find the specified file
in [0x00289] (at /home/jdong/dev/mono-1.1.7/mcs/class/System/System.Diagnostics/Process.cs:823) System.Diagnostics.Process:Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process)
in [0x00007] (at /home/jdong/dev/mono-1.1.7/mcs/class/System/System.Diagnostics/Process.cs:856) System.Diagnostics.Process:Start ()
in (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
in <0x0023a> Beagle.Tile.Tile:OpenFromMime (Beagle.Hit hit, System.String command_fallback, System.String args_fallback, Boolean expects_uris_fallback)
```
Gthumb:```
Open URI: action:_tile_86!Open
Cmd: '/usr/bin/gthumb'
Arg:  /home/burlap/obrazki/zdjecia/rocznica/zdjecia_rocznica/00001.jpg
Error in OpenFromMime: System.ComponentModel.Win32Exception: Cannot find the specified file
in [0x00289] (at /home/jdong/dev/mono-1.1.7/mcs/class/System/System.Diagnostics/Process.cs:823) System.Diagnostics.Process:Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process)
in [0x00007] (at /home/jdong/dev/mono-1.1.7/mcs/class/System/System.Diagnostics/Process.cs:856) System.Diagnostics.Process:Start ()
in (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
in <0x0023a> Beagle.Tile.Tile:OpenFromMime (Beagle.Hit hit, System.String command_fallback, System.String args_fallback, Boolean expects_uris_fallback)
```
Mozilla-firefox```
Open URI: action:_tile_205!Open
Cmd: '/usr/bin/mozilla-firefox'
Arg:  /home/burlap/dokumenty/worek/stare/kodeksy/html/Kdro/kdrogowy1.html
Error in OpenFromMime: System.ComponentModel.Win32Exception: Cannot find the specified file
in [0x00289] (at /home/jdong/dev/mono-1.1.7/mcs/class/System/System.Diagnostics/Process.cs:823) System.Diagnostics.Process:Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process)
in [0x00007] (at /home/jdong/dev/mono-1.1.7/mcs/class/System/System.Diagnostics/Process.cs:856) System.Diagnostics.Process:Start ()
in (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
in <0x0023a> Beagle.Tile.Tile:OpenFromMime (Beagle.Hit hit, System.String command_fallback, System.String args_fallback, Boolean expects_uris_fallback)
```

I would like to know if it is only my beagle, or is it a common problem. Also: whether this is Ubuntu dependecies issue or beagle bug (I will file it then)...

---

