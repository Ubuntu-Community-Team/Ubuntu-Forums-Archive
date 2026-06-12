---
title: "Help with Winrar &amp; Wine"
date: 2007-06-25
forum: General Help
---

### Post by WanderingKnight on 2007-06-25
The Winrar folder got deleted from my Wine directory some time ago (I can't remember under what circumstances). I now need to use it again, but when trying to install it I get this error:

> err:win:CreateWindowExA bad class name "RichEdit"
fixme:actctx:ActivateActCtx 0x175598 0x338ec8
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:ras:RasEnumEntriesW ((nil),(null),0x18b748,0x333a0c,0x18b434),stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ras:RasEnumEntriesW ((nil),(null),0x19b1d8,0x333a0c,0x18d3e4),stub!
err:win:CreateWindowExA bad class name "RichEdit"


I believe it has to do with it not being properly uninstalled. If so, how do I erase the winrar keys from the registry?

Thanks in advance.

---

### Post by r0ck80y on 2007-06-25
Havent used windows in a long time, so i dont remember where exactly the registry keys are stored. You can run "regedit" in console. This opens the windows-interface-like regedit tool. You can go to HKEY_CURRENT_USER --> Software and delete the winrar entry. This entry can also be found in .wine/user.reg. After that run "wineprefixcreate" in console to update registry. Try installing winrar after that. 
P.S. if you use winrar just to zip/unzip files, then you can install the "rar/unrar" utility through synaptic.

---

