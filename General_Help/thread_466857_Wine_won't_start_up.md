---
title: "Wine won't start up"
date: 2007-06-07
forum: General Help
---

### Post by sirana on 2007-06-07
I recently installed Wine to run some Windows software and in the process changed some of the settings in Wine (I changed some of the DLLs (shell32.dll, shlwapi.dll, shdocvw.dll) no native in order to make pacificpoker run).
Since then Wine doesn't start up and I don't know how to restore the original settings.
I tried deinstalling and reinstalling but it still doesn't start up.

I'm running ubuntu feisty with kernel 2.6.20-15-generic and I'm pretty much a linux n00b (my tinkering with the dlls probably told you that ;-)

thanks in advance

edited for clarification

---

### Post by anaconda on 2007-06-07
I guess some of the native dlls you installed to wine aren't compatible with wine..  but I think you already knew that :)

anyvay. If you can start winecfg and then remove the native dlls from there that would fix your problem.

If winecfg wont start then you just need to manually delete those .dll:s (eg. with rm) from where you copied them to. and then winecfg should start. They are propably in ~/wine/drive_c/windows/system32  -folder. 

You could also thry to remove them one by one, so you would find out which of the dll:s was incompatible..

PS. I would guess that the shell32.dll is the problem..

---

### Post by sirana on 2007-06-07
thank you for the fast response. 
ok this will sound stupid, but where would the wine folder be? because the only folder related to wine that I can see is usr/lib/wine and this is not what you meant, is it?

This is the error message that I get when I try to open winecfg:

err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library comdlg32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135


thanks again

---

### Post by trippinnik on 2007-06-07
should be /home/YOUR_USERNAME/.wine

you could also try sudo aptitude purge wine
and then reinstall it.  you may loose any of the programs that are installed though.

---

### Post by sirana on 2007-06-07
ok thanks a lot!

purged wine and manually deleted the files and now wine works again. 
thanks for the help

---

