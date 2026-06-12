---
title: "Wine Problem"
date: 2005-04-18
forum: General Help
---

### Post by Nez7165 on 2005-04-18
I have installed wine and started the setup and after setting up the the fake drive and it restartes it then fails
it say wineboot missing what do i do to sort this.

```
s\\Profiles\\Administrator"
Converted windows dir to new entry HKCU\Environment "windir" = L"c:\\windows"
Converted system dir to new entry HKCU\Environment "winsysdir" = L"c:\\windows\\system"
wine: cannot find 'wineboot'
Wine failed with return code 1
no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --new
Wine is not configured yet!
neil@NeilsPc:~$ sudo apt-get install wineboot
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
neil@NeilsPc:~$ sudo apt-get install wineboot
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wineboot
neil@NeilsPc:~$ clea
bash: clea: command not found
neil@NeilsPc:~$ clear

neil@NeilsPc:~$ winetools
found gettext in /usr/bin
Browser is /usr/bin/firefox.
rm: cannot remove `/home/neil/.wine/dosdevices/f:': Permission denied
no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Calls to wine are executed as wine.
Config is /home/neil/.wine/winetools.log.
CDROM is /media/cdrom0.
Choice is Base setup
Choice is Create a fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
rm: cannot remove `.wine/dosdevices/c:': Permission denied
rm: cannot remove `.wine/dosdevices/z:': Permission denied
rm: cannot remove `.wine/dosdevices/d:': Permission denied
rm: cannot remove `.wine/dosdevices/e:': Permission denied
rm: cannot remove `.wine/dosdevices/f:': Permission denied
rm: cannot remove `.wine/dosdevices/h:': Permission denied
rm: cannot remove `.wine/dosdevices/t:': Permission denied
rm: cannot remove directory `.wine/drive_c/My Documents/My Music': Permission denied
rm: cannot remove directory `.wine/drive_c/My Documents/My Pictures': Permission denied
rm: cannot remove directory `.wine/drive_c/My Documents/My Video': Permission denied
rm: cannot remove directory `.wine/drive_c/Program Files/Common Files': Permission denied
rm: cannot remove `.wine/drive_c/windows/command/start.exe': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/fonts': Permission denied
rm: cannot remove `.wine/drive_c/windows/inf/wine.inf': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/Administrator': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Desktop': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Temporary Internet Files': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/History': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Cookies': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Start Menu/Programs/StartUp': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/My Documents': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Favorites': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Recent': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/SendTo': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/NetHood': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Templates': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/PrintHood': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Start Menu/Programs/StartUp': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Desktop': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Favorites': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Application Data': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Templates': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Documents': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/Start Menu/Programs/Startup': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/Application Data': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/wcmd.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/control.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/help.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/notepad.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/progman.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/regsvr32.exe': Permission deniedrm: cannot remove `.wine/drive_c/windows/system/winmine.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/winver.exe': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/temp': Permission denied
rm: cannot remove `.wine/drive_c/windows/notepad.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/regedit.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/rundll32.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/uninstall.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/winhelp.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/winebrowser.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/win.ini': Permission denied
rm: cannot remove `.wine/drive_c/windows/system.ini': Permission denied
rm: cannot remove `.wine/drive_c/windows/winhlp32.exe.wine': Permission denied
rm: cannot remove `.wine/drive_c/config.sys': Permission denied
rm: cannot remove `.wine/drive_c/autoexec.bat': Permission denied
rm: cannot remove `.wine/drive_c/Programme': Permission denied
rm: cannot remove `.wine/drive_c/tmp': Permission denied
rm: cannot remove `.wine/drive_c/temp': Permission denied
rm: cannot remove `.wine/c': Permission denied
rm: cannot remove `.wine/system.reg': Permission denied
rm: cannot remove `.wine/userdef.reg': Permission denied
rm: cannot remove `.wine/user.reg': Permission denied
rm: cannot remove `.wine/fake_windows': Permission denied
rm: cannot remove `.wine/config': Permission denied
rm: cannot remove `.wine/winetools.log': Permission denied
mkdir: cannot create directory `/home/neil/.wine': File exists
cp: cannot create regular file `/home/neil/.wine/config': Permission denied
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/command/start.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/command/start.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/notepad.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/notepad.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/regedit.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/regedit.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/rundll32.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/rundll32.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/system/wcmd.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/system/wcmd.exerm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/system/control.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/system/control.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/system/help.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/system/help.exerm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/system/notepad.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/system/notepad.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/system/progman.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/system/progman.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/system/regsvr32.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/system/regsvr32.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/system/winmine.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/system/winmine.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/system/winver.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/system/winver.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/uninstall.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/uninstall.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/winhelp.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/winhelp.exe
ln: creating symbolic link `/home/neil/.wine/dosdevices/c:/windows/winhlp32.exe' to `/usr/lib/wine/winhelp.exe.so': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/winhlp32.exe
rm: cannot remove `/home/neil/.wine/dosdevices/c:/windows/winebrowser.exe': Permission denied
Warning: failed to create /home/neil/.wine/dosdevices/c:/windows/winebrowser.execp: cannot create regular file `/home/neil/.wine/dosdevices/c:/windows/inf/wine.inf': Permission denied
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
rm: cannot remove `.wine/dosdevices/c:': Permission denied
rm: cannot remove `.wine/dosdevices/z:': Permission denied
rm: cannot remove `.wine/dosdevices/d:': Permission denied
rm: cannot remove `.wine/dosdevices/e:': Permission denied
rm: cannot remove `.wine/dosdevices/f:': Permission denied
rm: cannot remove `.wine/dosdevices/h:': Permission denied
rm: cannot remove `.wine/dosdevices/t:': Permission denied
rm: cannot remove directory `.wine/drive_c/My Documents/My Music': Permission denied
rm: cannot remove directory `.wine/drive_c/My Documents/My Pictures': Permission denied
rm: cannot remove directory `.wine/drive_c/My Documents/My Video': Permission denied
rm: cannot remove directory `.wine/drive_c/Program Files/Common Files': Permission denied
rm: cannot remove `.wine/drive_c/windows/command/start.exe': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/fonts': Permission denied
rm: cannot remove `.wine/drive_c/windows/inf/wine.inf': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/Administrator': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Desktop': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Temporary Internet Files': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/History': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Cookies': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Start Menu/Programs/StartUp': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/My Documents': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Favorites': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Recent': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/SendTo': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/NetHood': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/Templates': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/root/PrintHood': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Start Menu/Programs/StartUp': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Desktop': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Favorites': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Application Data': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Templates': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/profiles/All Users/Documents': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/Start Menu/Programs/Startup': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/Application Data': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/wcmd.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/control.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/help.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/notepad.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/progman.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/regsvr32.exe': Permission deniedrm: cannot remove `.wine/drive_c/windows/system/winmine.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/system/winver.exe': Permission denied
rm: cannot remove directory `.wine/drive_c/windows/temp': Permission denied
rm: cannot remove `.wine/drive_c/windows/notepad.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/regedit.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/rundll32.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/uninstall.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/winhelp.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/winebrowser.exe': Permission denied
rm: cannot remove `.wine/drive_c/windows/win.ini': Permission denied
rm: cannot remove `.wine/drive_c/windows/system.ini': Permission denied
rm: cannot remove `.wine/drive_c/windows/winhlp32.exe.wine': Permission denied
rm: cannot remove `.wine/drive_c/config.sys': Permission denied
rm: cannot remove `.wine/drive_c/autoexec.bat': Permission denied
rm: cannot remove `.wine/drive_c/Programme': Permission denied
rm: cannot remove `.wine/drive_c/tmp': Permission denied
rm: cannot remove `.wine/drive_c/temp': Permission denied
rm: cannot remove `.wine/c': Permission denied
rm: cannot remove `.wine/system.reg': Permission denied
rm: cannot remove `.wine/userdef.reg': Permission denied
rm: cannot remove `.wine/user.reg': Permission denied
rm: cannot remove `.wine/fake_windows': Permission denied
rm: cannot remove `.wine/config': Permission denied
rm: cannot remove `.wine/winetools.log': Permission denied
tar: /usr/share/winetools/wineinit.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
cp: cannot create regular file `/home/neil/.wine/config': Permission denied
Invoking /usr/lib/wine/wine.bin rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf ...
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\amstream.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\atl.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system\\avifil32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\avifil32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\comcat.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\d3dxof.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\ddraw.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\devenum.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\oleaut32.dll") not found
err:module:import_dll Library oleaut32.dll (which is needed by L"c:\\windows\\system\\devenum.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dinput.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dmband.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dmcompos.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dsound.dll") not found
err:module:import_dll Library dsound.dll (which is needed by L"c:\\windows\\system\\dmime.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dmime.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dmloader.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dmscript.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dmstyle.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dmsynth.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dmusic.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dplayx.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dpnet.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dswave.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\dxdiagn.dll") not found
err:module:import_dll Loading library oleaut32.dll (which is needed by L"c:\\windows\\system\\dxdiagn.dll") failed (error c000007b).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\hhctrl.ocx") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\mlang.dll") not found
err:module:import_dll Loading library dsound.dll (which is needed by L"c:\\windows\\system\\quartz.dll") failed (error c000007b).
err:module:import_dll Loading library ddraw.dll (which is needed by L"c:\\windows\\system\\quartz.dll") failed (error c000007b).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\quartz.dll") not found
err:module:import_dll Loading library oleaut32.dll (which is needed by L"c:\\windows\\system\\quartz.dll") failed (error c000007b).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\urlmon.dll") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system\\urlmon.dll") failed (error c000007b).
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system\\wininet.dll") failed (error c000007b).
err:module:import_dll Loading library shell32.dll (which is needed by L"c:\\windows\\system\\wininet.dll") failed (error c000007b).
err:module:import_dll Library wininet.dll (which is needed by L"c:\\windows\\system\\urlmon.dll") not found
err:module:import_dll Library urlmon.dll (which is needed by L"c:\\windows\\system\\shdocvw.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\shdocvw.dll") not found
fixme:seh:EXC_RtlRaiseException call (from 0x7fcb4b2c) to unimplemented function shell32.dll.SHGetSpecialFolderPathW
wine: Unhandled exception (thread 0009), starting debugger...
err:seh:start_debugger Couldn't start debugger ("winedbg 8 80") (2)
Read the Wine Developers Guide on how to set up winedbg or another debugger
wineserver: could not save registry branch to /home/neil/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/neil/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/neil/.wine/user.reg : Permission denied
Wine exited with a successful status
changing link /home/neil/.wine/drive_c/windows/command/start.exe to /usr/lib/wine/start.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/command/start.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/system/wcmd.exe to /usr/lib/wine/wcmd.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/system/wcmd.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/system/control.exe to /usr/lib/wine/control.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/system/control.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/system/help.exe to /usr/lib/wine/winhelp.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/system/help.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/system/notepad.exe to /usr/lib/wine/notepad.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/system/notepad.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/system/progman.exe to /usr/lib/wine/progman.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/system/progman.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/system/regsvr32.exe to /usr/lib/wine/regsvr32.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/system/regsvr32.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/system/winmine.exe to /usr/lib/wine/winemine.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/system/winmine.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/system/winver.exe to /usr/lib/wine/winver.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/system/winver.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/notepad.exe to /usr/lib/wine/notepad.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/notepad.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/regedit.exe to /usr/lib/wine/regedit.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/regedit.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/rundll32.exe to /usr/lib/wine/rundll32.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/rundll32.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/uninstall.exe to /usr/lib/wine/uninstaller.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/uninstall.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/winhelp.exe to /usr/lib/wine/winhelp.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/winhelp.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/winebrowser.exe to /usr/lib/wine/winebrowser.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/winebrowser.exe': Permission denied
changing link /home/neil/.wine/drive_c/windows/winhlp32.exe.wine to /usr/lib/wine/winhelp.exe.so\'.so'.so
ln: cannot remove `/home/neil/.wine/drive_c/windows/winhlp32.exe.wine': Permission denied
mv: cannot stat `/home/neil/.wine/drive_c/windows/winhlp32.exe': No such file or directory
Drive C: is /home/neil/.wine/drive_c, links will be made for c fake_windows
ln: creating symbolic link `/home/neil/.wine/c/drive_c' to `/home/neil/.wine/drive_c': Permission denied
ln: creating symbolic link `/home/neil/.wine/fake_windows/drive_c' to `/home/neil/.wine/drive_c': Permission denied
cp: cannot create regular file `/home/neil/.wine/config': Permission denied
ln: creating symbolic link `/home/neil/.wine/dosdevices/d:/cdrom0' to `/media/cdrom0': Permission denied
ln: `/home/neil/.wine/dosdevices/t:/tmp': File exists
/usr/bin/winetools: line 222: /home/neil/.wine/winetools.log: Permission denied
touch: cannot touch `/home/neil/.wine/c/config.sys': Permission denied
touch: cannot touch `/home/neil/.wine/c/autoexec.bat': Permission denied
ln: creating symbolic link `/home/neil/.wine/drive_c/Programme/Program Files' to `/home/neil/.wine/c/Program Files': Permission denied
ln: `/home/neil/.wine/c/tmp/tmp': File exists
ln: `/home/neil/.wine/c/temp/tmp': File exists
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Invoking /usr/lib/wine/wine.bin wineboot ...
wine: cannot find 'wineboot'
wineserver: could not save registry branch to /home/neil/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/neil/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/neil/.wine/user.reg : Permission denied
Wine failed with return code 1
/usr/bin/wine: line 606: 12574 Terminated              $XMESSAGE -timeout 30 -buttons "    Dismiss    ":0," Never display this message again ":3 -title "Wine Launch Window" "Invoking $WINEBIN/$WINE_BIN_NAME $@ ...

        This dialog box is a temporary status dialog to let you know
        that Wine is attempting to launch your application.

        Since Wine is still very much in a development stage,
        many applications will fail silently.
        This dialog box is your indication
        that we're *trying* to run your application.

        This dialog box will automatically disappear after 30 seconds,
        or after your application finishes.

        You can permanently disable this dialog by selecting
        the option below.
        " 2>/dev/null
no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --new
Wine is not configured yet!
```

---

### Post by burlap on 2005-04-19
1. Do NOT run winetools as root.
2. Install wine-utils package (wineboot is there). 
3. Delete your .wine directory (you might need sudo to do that) and start again with winetools (WITHOUT sudo). 

```
sudo apt-get install wine-utils
sudo rm -ri /home/neil/.wine
winetools
```**(Remove will ask to confirm every single file - if you are sure about removing everything at once, use "sudo rm -r /home/neil/.wine")**

---

### Post by Nez7165 on 2005-04-19
Thanks it now gets further but still fails. on status 2 now. 

```
winetools
found gettext in /usr/bin
Browser is /usr/bin/firefox.
no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Calls to wine are executed as wine.
Config is /home/neil/.wine/winetools.log.
CDROM is .
Choice is Base setup
Choice is Create a fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Invoking /usr/lib/wine/wine.bin rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf ...
Converted temp dir to new entry HKCU\Environment "TEMP" = L"t:\\"
Converted path dir to new entry HKCU\Environment "PATH" = L"c:\\windows;c:\\windows\\system"
Converted profile dir to new entry HKCU\Environment "USERPROFILE" = L"c:\\windows\\Profiles\\Administrator"
Converted windows dir to new entry HKCU\Environment "windir" = L"c:\\windows"
Converted system dir to new entry HKCU\Environment "winsysdir" = L"c:\\windows\\system"
Wine exited with a successful status
/usr/bin/wine: line 609: 23304 Terminated              $XMESSAGE -timeout 30 -buttons "    Dismiss    ":0," Never display this message again ":3 -title "Wine Launch Window" "Invoking $WINEBIN/$WINE_BIN_NAME $@ ...

        This dialog box is a temporary status dialog to let you know
        that Wine is attempting to launch your application.

        Since Wine is still very much in a development stage,
        many applications will fail silently.
        This dialog box is your indication
        that we're *trying* to run your application.

        This dialog box will automatically disappear after 30 seconds,
        or after your application finishes.

        You can permanently disable this dialog by selecting
        the option below.
        " 2>/dev/null
/usr/bin/wineprefixcreate: line 174: wineserver: command not found
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Drive C: is /home/neil/.wine/drive_c, links will be made for c fake_windows
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Invoking /usr/lib/wine/wine.bin wineboot ...
Wine exited with a successful status
/usr/bin/wine: line 609: 23421 Terminated              $XMESSAGE -timeout 30 -buttons "    Dismiss    ":0," Never display this message again ":3 -title "Wine Launch Window" "Invoking $WINEBIN/$WINE_BIN_NAME $@ ...

        This dialog box is a temporary status dialog to let you know
        that Wine is attempting to launch your application.

        Since Wine is still very much in a development stage,
        many applications will fail silently.
        This dialog box is your indication
        that we're *trying* to run your application.

        This dialog box will automatically disappear after 30 seconds,
        or after your application finishes.

        You can permanently disable this dialog by selecting
        the option below.
        " 2>/dev/null
detecting Wine version... done.
Drive C: is /home/neil/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are Invoking /usr/lib/wine/wine.bin winepath.exe -l --new ...
winepath: invalid option L"--new"
Try 'winepath --help' for help
``` 

any ideas. i think its to do with the bottem part thanks.

---

### Post by Dromio on 2005-04-19
I had all sorts of issues with wine from the ubuntu repositories.  I'd suggest using the files from winehq instead, they've worked very well for me.  Look [here](http://winehq.com/site/download-deb) for instructions.

---

### Post by burlap on 2005-04-19
Well, I've had some problems running winetools and wine from ubuntu repositories, but finally I have all set up. 

There were some errors (like this one with "winepath"), but I think that it was ok just to run winetools again - errors didn't affect installation of software... 

I know this is a lousy explanation, so feel free to follow winehq instructions.

---

### Post by Nez7165 on 2005-04-19
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ thats were i downloaded it from. I was following this how to [http://www.ubuntuforums.org/showthread.php?t=27369&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=27369&page=1&pp=10)

im not sure wat i should do to use wine then

---

### Post by Nez7165 on 2005-04-19
i found a way and have installed a program and it seems to work fine. Dose wine support games or do i need 2 install winex as well.

[http://www.ubuntuforums.org/showthread.php?t=5458&highlight=wine+howto](http://www.ubuntuforums.org/showthread.php?t=5458&highlight=wine+howto)

this is how i did mine

---

### Post by true_friend on 2006-08-26
Nez7165: can u tell me how do u installed a program in wine. i could not do so in wine through wine tools.
plz help me in this regard.
thnx a lot advance :)

---

