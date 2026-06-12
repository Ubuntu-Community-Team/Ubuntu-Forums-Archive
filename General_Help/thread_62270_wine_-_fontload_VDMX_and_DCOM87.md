---
title: "wine - font:load_VDMX and DCOM87"
date: 2005-09-04
forum: General Help
---

### Post by earther on 2005-09-04
Wine is now installed (and configured with Sidenet) on my computer complete with IE and and My Computer icons on the desktop. But when I tried to install Photoshop, I got this error:

```
xxxxx@ubuntu:~$ wine /media/cdrom0/setup.exe
fixme:font:load_VDMX Failed to retrieve vTable
```The setup started but no fonts were displaying on the buttons or dialogue boxes.  (The fonts are missing in IE also.)  I poked around about the missing fonts and found this on Sidenet <http://sidenet.ddo.jp/winetips/config.html>

```
DCOM98 requires Windows98 licence. So, not all of wine users can
install that legally.
Wine builtin DCOM staffs are getting better. Please be patient;-)
If you have Windows98 licence, you can install DCOM98 with:

WINEDLLOVERRIDES="ole32=n" wine dcom98.exe
```I haven't a clue how to implement that command. I tried a few things but it spat back various failures.  FWIW, I have a Win 98 disk with serial in hand.  Does anyone know what's going on and how to fix it?  Thanks . . .

---

### Post by earther on 2005-09-04
Anyone?

---

### Post by arnieboy on 2005-09-04
[QUOTE=earther]Wine is now installed (and configured with Sidenet) on my computer complete with IE and and My Computer icons on the desktop. But when I tried to install Photoshop, I got this error:

```
xxxxx@ubuntu:~$ wine /media/cdrom0/setup.exe
fixme:font:load_VDMX Failed to retrieve vTable
```The setup started but no fonts were displaying on the buttons or dialogue boxes.  (The fonts are missing in IE also.)  I poked around about the missing fonts and found this on Sidenet <http://sidenet.ddo.jp/winetips/config.html>

```
DCOM98 requires Windows98 licence. So, not all of wine users can
install that legally.
Wine builtin DCOM staffs are getting better. Please be patient;-)
If you have Windows98 licence, you can install DCOM98 with:

WINEDLLOVERRIDES="ole32=n" wine dcom98.exe
```I haven't a clue how to implement that command. I tried a few things but it spat back various failures.  FWIW, I have a Win 98 disk with serial in hand.  Does anyone know what's going on and how to fix it?  Thanks . . .[/QUOTE]
u have to run the command in the directory u downloaded dcom98.exe or givethe full path name if u wanna run it from elsewhere. try this and let me know what errors u are getting

---

### Post by earther on 2005-09-04
[QUOTE=arnieboy]u have to run the command in the directory u downloaded dcom98.exe or givethe full path name if u wanna run it from elsewhere. try this and let me know what errors u are getting[/QUOTE]Thanks for the explanation. I was able to install DCOM98 but with these errors:
 
```
xxxxxx@ubuntu:~$ WINEDLLOVERRIDES="ole32=n" wine ~/dcom98.exe
fixme:setupapi:SETUPX_CreateStandardLDDs LDID_SRCPATH: what exactly do we have to do here ?
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:vcpUICallbackProc16 (0xf740, 0705, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070f, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 0710, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070b, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070c, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:rpc:RPCRT4_DllRegisterServer (): stub
```Some things are running more smoothly but when I tried to install PS, I am still getting this error and most of the fonts on sites viewed in IE6 are missing:

```
xxxxx@ubuntu:~$ wine /media/cdrom0/setup.exe
fixme:font:load_VDMX Failed to retrieve vTable
```Any more advice?

---

### Post by arnieboy on 2005-09-04
[QUOTE=earther]Thanks for the explanation. I was able to install DCOM98 but with these errors:
 
```
xxxxxx@ubuntu:~$ WINEDLLOVERRIDES="ole32=n" wine ~/dcom98.exe
fixme:setupapi:SETUPX_CreateStandardLDDs LDID_SRCPATH: what exactly do we have to do here ?
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:vcpUICallbackProc16 (0xf740, 0705, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070f, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 0710, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070b, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070c, 0000, 00000000, 7bc25a54) - semi-stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:rpc:RPCRT4_DllRegisterServer (): stub
```Some things are running more smoothly but when I tried to install PS, I am still getting this error and most of the fonts on sites viewed in IE6 are missing:

```
xxxxx@ubuntu:~$ wine /media/cdrom0/setup.exe
fixme:font:load_VDMX Failed to retrieve vTable
```Any more advice?[/QUOTE]

save the attached file as config (NOT config.txt) in @HOME/.wine and tell me if u see any difference when u run the install again.

also a good reference point is:
[http://frankscorner.org/](http://frankscorner.org/)

---

### Post by earther on 2005-09-04
[QUOTE=arnieboy]save the attached file as config (NOT config.txt) in @HOME/.wine and tell me if u see any difference when u run the install again.[/QUOTE]I don't have .wine in the home folder or anywhere else!  There is a /home/xxxx/wine-config-sidenet/wineconfig folder that has config.safe (for base installation) and config.sidenet.  I relaced you the config.sidenet with your file (renamed) and it made no difference.  Should I replace the file and then run DCOM98 again?  I've attached the renamed config.sidenet file below.

---

### Post by arnieboy on 2005-09-04
[QUOTE=earther]I don't have .wine in the home folder or anywhere else!  There is a /home/xxxx/wine-config-sidenet/wineconfig folder that has config.safe (for base installation) and config.sidenet.  I relaced you the config.sidenet with your file (renamed) and it made no difference.  Should I replace the file and then run DCOM98 again?  I've attached the renamed config.sidenet file below.[/QUOTE]
are u sure there is no .wine folder in your home directory?
try doing a ```
cd $HOME/.wine
``` from terminal

---

### Post by earther on 2005-09-04
[QUOTE=arnieboy]are u sure there is no .wine folder in your home directory?[/QUOTE]Duh, there were a LOT of hidden folders and files!  There are .wine and .wine.0509031642 folders.  Both have config files. Here is the one from .wine.

---

