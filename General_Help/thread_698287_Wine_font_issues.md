---
title: "Wine font issues"
date: 2008-02-16
forum: General Help
---

### Post by derrekito on 2008-02-16
Some font is  broken regarding wine. I attached an image of my problem.  

Thanks in advanced,
-Derrek

---

### Post by happyhamster on 2008-02-16
Try installing the windows truetype fonts:

sudo apt-get install msttcorefonts

---

### Post by derrekito on 2008-02-16
I already had them installed.  These fonts were working previously, however now they are not.

---

### Post by happyhamster on 2008-02-16
Which wine version are you using? Did you recently upgrade wine (or did anyhting else change in its setup)? Have you installed that application before (with text showing)? Which error messages appear in the terminal?

- If you're using a dvd/cd: try running the setup.exe from within its folder, instead of using the full path (wine setup.exe instead of wine /media/cdrom0/setup.exe).
- Also: search the disc for alternative setup-executables, and look for custom fonts too (.fon or .ttf specifically). Look into any relevant .ini file to see if the setup needs anything special (paths, pre-installed dll-files*, etc).
- Just a long shot: perhaps the text and background have the same color.
- Try running the setup executable in a windowed wine instead of fullscreen. (run "winecfg" to change this)


* If you run the executable like this:

WINEDEBUG=fixme-all,+loaddll wine setup.exe

you can check which built-in/native-dll files are used while running the program.


Good luck, and keep us informed.

---

### Post by derrekito on 2008-02-16
I am always using the latest release from the Wine Ubuntu repository.

```
WINEDEBUG=fixme-all,+loaddll wine setup.exe >> /home/derrekito/Desktop/wine_error
```

doing this builds a blank txt doc (i'm trying to give you all of the feed back when running it).  What am I forgetting?

**Below** is all I can get from the console history:
```
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da68) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d794) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d798) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34e050) stub!
fixme:process:IsWow64Process (0xffffffff 0x34e024) stub!
fixme:process:IsWow64Process (0xffffffff 0x34e024) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341144) stub!
fixme:process:IsWow64Process (0xffffffff 0x341534) stub!
fixme:reg:GetNativeSystemInfo (0x341510) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x341704) stub!
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x1b0042
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000000
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070057
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2f00-000035000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3100-000035000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2f00-000035000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2f00-000035000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2f00-000035000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2f00-000035000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2f00-000035000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2f00-000035000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108

derrekito@beastie:/media/cdrom0$ WINEDEBUG=fixme-all,+loaddll wine setup.exe >> /home/derrekito/Desktop/wine_error
trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_native_dll Loaded L"F:\\setup.exe" at 0x400000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\lz32.dll" at 0x7ee70000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\version.dll" at 0x7ee80000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7ec50000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\gdi32.dll" at 0x7eca0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\user32.dll" at 0x7ed40000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shlwapi.dll" at 0x7eaf0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\comctl32.dll" at 0x7ea30000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shell32.dll" at 0x7eb50000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\iphlpapi.dll" at 0x7e910000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rpcrt4.dll" at 0x7e930000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ole32.dll" at 0x7e990000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\oleaut32.dll" at 0x7e850000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "system.drv" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winex11.drv" at 0x7e650000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\imm32.dll" at 0x7da20000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\uxtheme.dll" at 0x7d9e0000: builtin
trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\temp\\set7092.tmp" at 0x400000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\lz32.dll" at 0x7ee60000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\version.dll" at 0x7ee90000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7ec40000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\gdi32.dll" at 0x7ec90000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\user32.dll" at 0x7ed30000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shlwapi.dll" at 0x7eaf0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\comctl32.dll" at 0x7ea20000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shell32.dll" at 0x7eb40000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\iphlpapi.dll" at 0x7e900000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rpcrt4.dll" at 0x7e930000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ole32.dll" at 0x7e990000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\oleaut32.dll" at 0x7e840000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "system.drv" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
derrekito@beastie:/media/cdrom0$ trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winex11.drv" at 0x7e640000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\imm32.dll" at 0x7da10000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\uxtheme.dll" at 0x7d9d0000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\11\\50\\Intel32\\setup.dll" at 0x10000000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\crypt32.dll" at 0x7d500000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rsabase.dll" at 0x7d4e0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rsaenh.dll" at 0x7d4b0000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\11\\50\\Intel32\\iGdi.dll" at 0x3b0000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\temp\\isp71cc.tmp\\_Setup.dll" at 0x860000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\cabinet.dll" at 0x7d430000: builtin
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\cabinet.dll" : builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\Objectps.dll" at 0x350000: native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\Objectps.dll" : native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\11\\50\\Intel32\\iKernel.dll" at 0x8b0000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\stdole2.tlb" at 0x7d440000: builtin
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\stdole2.tlb" : builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\objectps.dll" at 0x360000: native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\objectps.dll" : native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\11\\50\\Intel32\\ctor.dll" at 0xd00000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\11\\50\\Intel32\\iscript.dll" at 0xe30000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winspool.drv" at 0x7d420000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\ISRT.dll" at 0x13d0000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RICHED20.dll" at 0x77300000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RICHED32.DLL" at 0x76be0000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winmm.dll" at 0x7d060000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\11\\50\\Intel32\\iuser.dll" at 0x1550000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winealsa.drv" at 0x7d030000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\msacm32.dll" at 0x7cf40000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\msacm32.drv" at 0x7d400000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\midimap.dll" at 0x7cf20000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\objectps.dll" at 0x17b0000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\_isres.dll" at 0x17f0000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\_isuser.dll" at 0x1990000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\ORSETU32.DLL" at 0x1ce0000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ws2_32.dll" at 0x7cdc0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\netapi32.dll" at 0x7cdf0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\comdlg32.dll" at 0x7cd20000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\LIBINS32.DLL" at 0x2210000: native
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000000
trace:loaddll:free_modref Unloaded module L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\ORSETU32.DLL" : native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\LIBINS32.DLL" : native
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\comdlg32.dll" : builtin
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\netapi32.dll" : builtin
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\ws2_32.dll" : builtin
trace:loaddll:free_modref Unloaded module L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\_isres.dll" : native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\_isuser.dll" : native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\temp\\{1542276E-DCA8-11DC-F989-001D60B168A5}\\{EFDB311E-5323-44B7-8472-BAB649C1C80D}\\ISRT.dll" : native
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\winspool.drv" : builtin
trace:loaddll:free_modref Unloaded module L"C:\\windows\\temp\\isp71cc.tmp\\_Setup.dll" : native
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\rsabase.dll" : builtin
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\11\\50\\Intel32\\setup.dll" : native
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070057
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3e00-00000e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-4700-00000e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3e00-00000e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3e00-00000e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3e00-00000e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3e00-00000e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3e00-00000e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3e00-00000e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\objectps.dll" : native
```

I also wanted to mention that the fonts are broken for the wine config gui utility.

---

### Post by happyhamster on 2008-02-16
Redirecting should work using:

WINEDEBUG=fixme-all,+loaddll wine setup.exe &> /home/derrekito/Desktop/wine_error

---

### Post by derrekito on 2008-02-16
> **happyhamster said:**
> Redirecting should work using:

WINEDEBUG=fixme-all,+loaddll wine setup.exe &> /home/derrekito/Desktop/wine_error

That did the trick! So here is the output from running setup.exe under wine:

---

### Post by happyhamster on 2008-02-16
- If fonts are broken for wine as a whole, then I would personally just re-install wine completely. If that's not an option then first try removing and re-installing msttcorefonts:

sudo apt-get remove --purge msttcorefonts
sudo apt-get install msttcorefonts

- If that didn't work, you should try making a fresh wine "bottle" to see if the problem persists:

wineprefixcreate --prefix ~/.choose-a-name

- This will create a completely new wine-setup in the folder ".choose-a-name" in your home dir, next to the default .wine folder. (If you want to get rid of it later, just delete the folder.)
- To use wine and winecfg with that fresh setup, you have to point to it like this:

env WINEPREFIX="/$HOME/.choose-a-name" winecfg

- That line will run a fresh winecfg. If even that winecfg doesn't show any text, then you could try a fix: make a text file containing only:

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

- Save it as file-name.reg (or whatever), and import it into the wine registry:

wine regedit file-name.reg

(see: [http://wiki.winehq.org/FAQ#head-6b53a75005c4428f7bd0cd355ebbe1c74093f688](http://wiki.winehq.org/FAQ#head-6b53a75005c4428f7bd0cd355ebbe1c74093f688))


- Anyway, if you choose to completely re-install wine:

sudo apt-get remove --purge wine

- Delete or move the hidden .wine folder in your home dir (to see hidden files: press ctrl-h in nautilus) and re-install.

Good luck.

---

### Post by derrekito on 2008-02-16
It isn't fonts completly.  For example once in an application fonts appear, it seems to be isolated to situations such as install shield and wineconfig.  I'm wondering if it is ONE font.  I shall try to reinstall ms fonts.
...
...
```
All done, no errors.
All fonts downloaded and installed.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
Couldn't get cwd: No such file or directory

```

Still broken.  I shall try the wine bottle approach.
...
...

**The bottle workes!**  So any clue as to what I did to break the old one?  :p

I just reinstalled wine, but the programs and the such did not go away (and neither did my problem).  What is the best way to go clean with wine?

---

### Post by happyhamster on 2008-02-16
> **derrekito said:**
> **The bottle workes!**  So any clue as to what I did to break the old one?  :p
Perhaps some application installed a font of its own which caused a conflict, I don't know. Wine works in mysterious ways... :)

> I just reinstalled wine, but the programs and the such did not go away (and neither did my problem).  What is the best way to go clean with wine?
Delete the hidden .wine folder in your home dir (hidden folders have names starting with a dot). Then update wine using the command:

wineprefixcreate

To create a fresh one. That should be enough.

---

### Post by derrekito on 2008-02-16
Thank you!  You are a bad ***.

-Derrek

---

