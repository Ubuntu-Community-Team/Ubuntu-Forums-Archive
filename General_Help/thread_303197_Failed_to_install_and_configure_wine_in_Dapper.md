---
title: "Failed to install and configure wine in Dapper"
date: 2006-11-19
forum: General Help
---

### Post by robli99 on 2006-11-19
I am trying to install Wine onto Dapper. I used apt-get to install wine. Installation is smoothly, but winecfg failed. I search the forum, and follow someone's instruction, step by step, repeated uninstall-install-wincfg. winecfg never succeeded.
Someone said the erro is caused by audio card. My audio is intel HDA, integrated on motherboard. Driver is ALSA. I notised, after I installed wine, the sound became very very low. I opened the volume adjustment panel, after I clicked and slided every buttom to maximum many times, the volume level became normal.

Following is the error message.
=================================================
root@ljz-linux:~# winecfg 
wine: creating configuration directory '/root/.wine'... 
Unknown device ID 5B60, please report. Assuming plain R300. 
*********************************WARN_ONCE********************************* 
File r300_state.c function r300Enable line 456 
TODO - double side stencil ! 
*************************************************************************** 
No ctx->FragmentProgram._Current!! 
Unknown device ID 5B60, please report. Assuming plain R300. 
*********************************WARN_ONCE********************************* 
File r300_state.c function r300Enable line 456 
TODO - double side stencil ! 
*************************************************************************** 
No ctx->FragmentProgram._Current!! 
Unknown device ID 5B60, please report. Assuming plain R300. 
*********************************WARN_ONCE********************************* 
File r300_state.c function r300Enable line 456 
TODO - double side stencil ! 
*************************************************************************** 
No ctx->FragmentProgram._Current!! 
Failed to open the service control manager. 
===============================================


Sometime, winecfg will open the configure panel of wine after waiting of about 30 sec. but the panel just hang there and I can't even close it unless "kill" it.

Pls anybody have any idea?

---

### Post by dcstar on 2006-11-20
> **robli99 said:**
> 
......
Following is the error message.
=================================================
root@ljz-linux:~# winecfg 
......

Never, ever, use wine as root, you should use it as a normal user.

---

### Post by robli99 on 2006-11-20
Even when I used it as a normal user, I got the same error message.

---

