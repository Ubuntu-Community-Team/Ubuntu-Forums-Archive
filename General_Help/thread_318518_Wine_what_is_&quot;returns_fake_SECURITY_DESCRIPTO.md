---
title: "Wine: what is &quot;returns fake SECURITY_DESCRIPTOR&quot;?"
date: 2006-12-14
forum: General Help
---

### Post by dearephesus64 on 2006-12-14
Mere curiosity ensues:

Could anyone please explain basically what wine means when it says "returns fake SECURITY_DESCRIPTOR", and if there is hope of a workaround in the future?

It came up for me when installing Flash 9.0 for windows with wine, in order that Firefox 1.5.0.8 for windows and other wine/windows programs would play flash properly.  I know flash and Firefox are native now, but I wanted to see if it worked better.  Hence, the post is obviously not urgent.  Anyway, there seem to be a number of other programs that trigger the same warning.  

It's less vague and menacing than "destroy child object" or other things that wine spits out from time to time, but I'd still like to know what it's talking about and if this is something that can be fixed through the open source process.  

I am supposing that it's an error- it might just be wine informing me of something that it's doing to fool the program into believing it's running on windows.  

> joe@joe-laptop:~/Desktop$ wine install_flash_player.exe
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF1a8d.tmp") : returns fake SECURITY_DESCRIPTOR
fixme:advapi:GetFileSecurityW (L"c:\\Program Files\\Mozilla Firefox\\Plugins\\NPSWF32.dll") : returns fake SECURITY_DESCRIPTOR
fixme:advapi:GetFileSecurityW (L"c:\\Program Files\\Mozilla Firefox\\Plugins\\NPSWF32_FlashUtil.exe") : returns fake SECURITY_DESCRIPTOR
fixme:advapi:GetFileSecurityW (L"c:\\Program Files\\Mozilla Firefox\\Components\\flashplayer.xpt") : returns fake SECURITY_DESCRIPTOR
joe@joe-laptop:~/Desktop$

(the system is running Wine 0.9.22/Kubuntu Edgy)

---

