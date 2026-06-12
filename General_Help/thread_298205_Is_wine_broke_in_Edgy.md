---
title: "Is wine broke in Edgy???"
date: 2006-11-12
forum: General Help
---

### Post by phinn on 2006-11-12
I did:   sudo apt-get install wine  as per the Edgy documentation


Am I missing something?  Everything I try and wine does absolutely nothing. It just sits there.  When I had it compiled from source a while back I had no such issues. ](*,)

---

### Post by nikhilk on 2006-11-12
Are you sure you have done "winecfg" after the installation? Just wanted to confirm that.

---

### Post by phinn on 2006-11-12
Oh I should have said that, yes I did  winecfg and everytime I try add the drive_c and click okay it doesn't save anything. Maybe thats whats wrong. 

Just get tons of warnings:
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/phinn', starting in the Windows directory.
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '../drive_c'


I have basically a default Edgy installation but I'm running Compiz/XGL, would that impact it?

---

### Post by nikhilk on 2006-11-12
I do not think that having Compiz/Berly etc should affect winecfg. At what point does winecfg crash, running it through a terminal will show error messages? Atleast, is the fake C drive being created sucessfully?

---

### Post by phinn on 2006-11-12
Okay I manually added a drive_c and a few things are working now. But still has issues.  Very weird stuff though

---

### Post by syadnom on 2006-11-12
zero problems with wine via automotix2 in edgy.  XGL/ATI also but i dont think it matters

just an FYI, it should work....maybe nuke all the wine stuff and start over with automatix2?

---

### Post by [bigmac] on 2006-11-13
Hi phinn, I have the exact same problem. I'm curious to know, how you managed to add a c_drive? Could you write what you did, if you remember it.

I can get it to work with default settings though, but i want my c_drive to be on a harddisk dedicated for games, instead of in the /home folder.

Howto's speak of a wine.conf in /etc say, but i don't have one...

---

### Post by BlackRoseBud on 2006-11-13
wine works fine for me on edgy.  I used automatix to install it and found the c_drive in a hidden .wine folder in my home directory.  Then I just right click the .exe file I want to run, click "Open with other application", click  "Use custom command" and type wine.

---

### Post by temcat on 2006-11-13
BTW, has anybody here managed to successfully install Office 2000 under Wine? It installs without complaints for me, but then I don't find a half of needed files in its installation directory.

---

### Post by frodon on 2006-11-13
Please read this nice documentation and don't forget to configure wine before using it :
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by todoporron on 2006-11-28
Same happens to me. I installed wine via synaptic and tied also the automatix 2 install. None of them work.

Result of Winecfg:
```
~$ winecfg
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Loading library comctl32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\winspool.drv") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\winspool.drv") failed (error c000007a).
err:module:import_dll Library winspool.drv (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007a).
err:module:import_dll Library comdlg32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library comctl32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library shell32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\winmm.dll") failed (error c000007b).
err:module:import_dll Library winmm.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\uxtheme.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\uxtheme.dll") failed (error c000007a).
err:module:import_dll Library uxtheme.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": /home/emerson/OpenFOAM/linux/gcc-4.1.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/../lib/libstdc++.so.6)
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135

```

Any suggestions?

---

