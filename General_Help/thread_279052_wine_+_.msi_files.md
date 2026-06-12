---
title: "wine + .msi files"
date: 2006-10-17
forum: General Help
---

### Post by orsula on 2006-10-17
Hi,
I am trying to install a .msi file using wine on Dapper Drake. I installed 
the msi installer with:

wine instmsia.exe

I added the following line to the DLL overides using winecfg:

"msi" = "native, builtin" "msiexec.exe" = "native, builtin"

I then installed the windows software with:

wine msiexec /i msifile.msi

(The software is a scientific image processing tool WinSPM from JEOL)

The installations worked perfectly it seemed. When I went to try and run the application with:

wine file.exe

I got the folloing errors:

err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\WinSPM_DPS211E\\WinSPM_ProcFunction.dll") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\WinSPM_DPS211E\\WinSPM_ProcFunction.dll") not found
err:module:import_dll Library WinSPM_ProcFunction.dll (which is needed by L"C:\\Program Files\\WinSPM_DPS211E\\WinSPM_ProcFunction.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\WinSPM_DPS211E\\WinSPM_ProcFunction.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\WinSPM_DPS211E\\WinSPM_ProcFunction.exe" failed, status c0000135


How do I fix/repair those DLL's?

Thanks very much

Gideon

---

### Post by gringer on 2007-05-25
It's probably complaining about missing DLLs as a side-effect of the DLL override settings that you are using. I have noticed that my [clean] wine installation already has msiexec.exe, so try using that first.

i.e. :
```

$ mv ~/.wine ~/.wine_old
$ wine msiexec.exe /i msifile.msi
```

If you get issues with installation after that, *then* you have a better chance of the bug being nailed down in the wine source code.

---

### Post by mihas on 2007-05-27
I get this error:

> 
~$ mv ~/.wine ~/.wine_old
~$ wine msiexec.exe /i msifile.msi
Invoking /usr/lib/wine/wine.bin msiexec.exe /i msifile.msi ...
wine: creating configuration directory '/home/miha7/.wine'...
Failed to open the service control manager.
wine: '/home/miha7/.wine' created successfully.
err:msi:copy_package_to_temp failed to copy package L"msifile.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!
Wine failed with return code 91

---

### Post by HerrAschen on 2007-12-06
Hey, this entire post helped me A LOT.  I've been trying to figure out how to install an MSI file for about a week now.  Thanks!

:guitar:

---

