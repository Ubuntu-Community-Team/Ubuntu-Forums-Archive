---
title: "Another Wine topic"
date: 2007-04-05
forum: General Help
---

### Post by Shmifty on 2007-04-05
I had Wine installed before on my system,, but I decided to remove it. Well it turns out that I want to use it now so I installed and tried to run an executable (like the iwki said to) and I get this error

> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/bryan/Desktop', starting in the Windows directory.


---

### Post by Shmifty on 2007-04-05
Someone has to have a remedy for this....

---

### Post by Shay Stephens on 2007-04-05
have you run winecfg to reinitialize the windows environment?

In the terminal it is
```
winecfg
```
once the config window pops up, you can close it unless you know you need to make some changes.  Once closed you can try to run your program again.

---

### Post by Shmifty on 2007-04-05
I opened winecfg but it gave me this error

> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/bryan/Desktop', starting in the Windows directory.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.


I have tried uninstalling and reinstalling, but nothing seems to be working.

---

### Post by Shay Stephens on 2007-04-05
have you tried deleting the .wine folder in your home directory?  If not, try that, then rerun winecfg.  The .wine folder is hidden, you you will have to show hidden folders to see it.

---

### Post by Shmifty on 2007-04-06
Okay I got wine to configure correctly, but now I have installed iTunes and am trying to run it, but I get this error:

> bryan@bryan-desktop:~/.wine/drive_c/Program Files/iTunes$ wine iTunes.exe
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1a5848) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1953a8)->((nil),00000008)
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33eea0
fixme:wintrust:WTHelperProvDataFromStateData (nil)
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33eea0
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1953a8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


---

### Post by tbroderick on 2007-04-06
[http://appdb.winehq.org/appview.php?iVersionId=4450](http://appdb.winehq.org/appview.php?iVersionId=4450)

---

