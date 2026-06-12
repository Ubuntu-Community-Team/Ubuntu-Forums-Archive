---
title: "Having trouble installing things with Wine"
date: 2008-05-04
forum: General Help
---

### Post by UbFido on 2008-05-04
Hey guys. I recently got Ubuntu 8.04 (Hardy Heron) going and its working just great!
- I then installed Wine and was gonna try and install MSN on it but when i right click the install file in the file manager and select run with wine i get "Error 8003" "Fatal error, the installation cannot continue" before the install shield even opens.

this:

bjho3@dell830-bjho3:/tmp$ wine msgpluslive-460.exe
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)

[1]+  Stopped                 wine msgpluslive-460.exe

Any help?

- Bjørn Zeiler

[EDIT] APPARENTLY i cannot run anything with wine ...
this error also came up when i did winecfg.
the Wine configuration window, opened after some time though, but terminal says this:

bjho3@dell830-bjho3:~$ winecfg
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
 

fixme:winspool:AddPrinterW DocumentPropertiesW on printer L"Laser_Printer_3100cn" fails
fixme:winspool:AddPrinterW DocumentPropertiesW on printer L"PDF" fails
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:shell:SHGetFolderPathW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Desktop".

Still, any help? ;D

---

### Post by TeoBigusGeekus on 2008-05-04
Not all window$ programs run with wine...
[http://appdb.winehq.org/appview.php?iAppId=127]("http://appdb.winehq.org/appview.php?iAppId=127")

---

### Post by TeoBigusGeekus on 2008-05-04
How did you install wine?

---

### Post by UbFido on 2008-05-04
i installed wine using the guide on the website
winehq.com ?

[EDIT] AND i see that msn apparenly doesnt work with Linux anyway?
But still. That doesnt explain why i cant do winecfg without getting the odd error?

- Bjørn Zeiler

---

### Post by TeoBigusGeekus on 2008-05-04
> **UbFido said:**
> i installed wine using the guide on the website
winehq.com ?

Does this mean that you used the synaptic package manager?

---

### Post by UbFido on 2008-05-04
Hmm...
I recall using the terminal to do it.
yea,.. im pretty sure i used the terminal ..
Or ? 
Does it matter ? ;D

- Bjørn Zeiler

---

### Post by TeoBigusGeekus on 2008-05-04
If it was 
sudo apt-get install wine
it doesn't matter, otherwise... I don't know.

Anyway, you can always do a complete uninstall through Synaptic and reinstall it.

---

### Post by UbFido on 2008-05-04
yes it was the sudo apt-get.
I recall now.

- Bjørn Zeiler

---

### Post by UbFido on 2008-05-04
right so i did a COMPLETE uninstall of wine and then i reinstalled it using:
sudo apt-get update
sudo apt-get install wine..

And then i did this again, and got:

bjho3@dell830-bjho3:/tmp$ wine msgpluslive-460.exe
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\My Documents".
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:mshtml:register_server RegInstall failed: 80004005
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:qmgr:register_server RegInstall failed: 80004005
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:setupapi:create_fake_dll failed to create L"C:\\windows\\explorer.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\hh.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\notepad.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\regedit.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\twain_32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\winhelp.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\command\\start.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\actxprxy.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\advapi32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\advpack.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\cabinet.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\cmd.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\comctl32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\comdlg32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\control.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\crypt32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\d3d8.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\d3d9.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\dbghelp.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\ddhelp.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\ddraw.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\dosx.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\dsound.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\dsound.vxd" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\gdi32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\hhctrl.ocx" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\imaadp32.acm" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\imagehlp.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\itircl.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\itss.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\kernel32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\msadp32.acm" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\msg711.acm" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\mshtml.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\msi.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\msiexec.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\msvcrt.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\msxml3.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\notepad.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\ntdll.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\ole32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\oleaut32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\oledlg.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\olepro32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\opengl32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\progman.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\psapi.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\quartz.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\regsvr32.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\riched20.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\riched32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\rpcrt4.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\rsabase.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\rsaenh.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\rundll32.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\schannel.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\setupapi.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\shdocvw.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\shell32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\shfolder.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\shlwapi.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\urlmon.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\user32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\version.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\winebrowser.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\wininet.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\winmm.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\winspool.drv" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\winver.exe" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\ws2_32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\wsock32.dll" (error=3)
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\drivers\\mountmgr.sys" (error=3)
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\Program Files".
fixme:setupapi:get_csidl_dir CSIDL 26 not found
err:setupapi:create_fake_dll failed to create L"C:\\windows\\system32\\unknown\\Internet Explorer\\iexplore.exe" (error=3)
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\Program Files\\Common Files".
fixme:setupapi:get_csidl_dir CSIDL 2b not found
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Application Data".
fixme:setupapi:get_csidl_dir CSIDL 1a not found
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\windows\\profiles\\bjho3\\Local Settings\\Application Data".
fixme:setupapi:get_csidl_dir CSIDL 1c not found
wine: configuration in '/home/bjho3/.wine' has been updated.
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"

Woot?
- Bjørn Zeiler

(I didnt do anything to winecfg yet this time, cause i have no idea of what to do?)

---

### Post by TeoBigusGeekus on 2008-05-04
Jesus...
I don't know what to say...
Sorry mate but my Ubuntu knowledge stops here.
Someone else please?

---

### Post by UbFido on 2008-05-05
Anyone?

---

### Post by UbFido on 2008-05-06
Someone?! :O

---

### Post by mc4man on 2008-05-06
Why don't you try it once more from start, open up synaptic, search wine and do a complete removal. Then for heck of it ck. home dir. (show hidden files) and see if there is a .wine dir. (shouldn't be, if there is delete it ) Then go back to synaptic, search wine and install. (should be ver. 0.9.59) After the install is complete run ```
winecfg
``` from terminal. If you get a preloader error see here
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)  do that and then run winecfg again. 
If you update wine in the future after the update is done run wineprefixcreate from terminal right after the update completes

---

### Post by UbFido on 2008-05-07
Right. So i did a complete uninstall and DAMN RIGHT there was a .wine directory. 
Deleted it and did a reinstall
put this in terminal:

```
bjho3@itdriften:~$ winecfg
wine: created the configuration directory '/home/bjho3/.wine'
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/bjho3/.wine' has been updated.
bjho3@itdriften:~$ 

```

I'm guessing thats a good sign? :)

- Bjørn Zeiler

---

### Post by mc4man on 2008-05-07
> I'm guessing thats a good sign
you should be good to go
don't worry about the Mozilla thing

---

