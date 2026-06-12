---
title: "Software for trading"
date: 2012-12-22
forum: General Help
---

### Post by legowo on 2012-12-22
I  want to do trading on linux operating system, I use linux ubuntu 11.10, and we know that the MT4 (Meta Trader) is only provided for  Windows platforms,
My first solution uses the emulator (WINE),
the installation process is not an error, only when running MT4 error message like this


 fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\InstaTrader\\sounds\\alert.wav") stub
linuxmint Downloads # err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\InstaTrader\\terminal.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\InstaTrader\\terminal.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\InstaTrader\\terminal.exe" failed, status c0000135


 What should I do?

---

### Post by legowo on 2012-12-22
I need You, truely

---

### Post by howefield on 2012-12-22
Try this [http://forum.winehq.org/viewtopic.php?t=14264](http://forum.winehq.org/viewtopic.php?t=14264)

But better would be to find a native client, which is likely to perform better.

Are you running Ubuntu 11.10 or Linux Mint ?

---

### Post by Wim Sturkenboom on 2012-12-22
You can start with [http://wiki.winehq.org/FAQ#head-2697b3c2437625eb387ae7360d9b224be0d20bce](http://wiki.winehq.org/FAQ#head-2697b3c2437625eb387ae7360d9b224be0d20bce)

And check in [http://appdb.winehq.org/](http://appdb.winehq.org/) if others have experience with your application under Wine.

---

