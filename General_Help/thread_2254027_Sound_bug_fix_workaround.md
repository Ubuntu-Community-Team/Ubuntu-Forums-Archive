---
title: "Sound bug fix workaround?"
date: 2014-11-24
forum: General Help
---

### Post by Douglas_H_Campbell on 2014-11-24
Looks like my sound problem has been fixed but I don't know what to do now.  Can someone explain to an novice in detail what
I should do now re:adding script.
Here's bug fix.Bug description: No sound in Linux after rebooting from Windows 8.1 Pro. Sound in Windows works normally.
> OK, now the fix patch landed in sound git tree for 3.18-rc5. > 
> Unfortunately, backporting this to stable kernels isn't so trivial.  Either
> we need to backport lots of other patches or we need to rewrite the code. 

Thank you for your attention. The bug is not critical. The can be a workaround with adding the script during the
system startup
. hda-verb /dev/snd/hwC0D2 0x20 SET_COEF_INDEX 0x07 

hda-verb /dev/snd/hwC0D2 0x20 SET_PROC_COEF 0x7cb0

---

### Post by pqwoerituytrueiwoq on 2014-11-24
if you are asking how to install the 3.18 kernel here is a script to do it, run it in a terminal with bash
[http://pastebin.com/1WFT28g9](http://pastebin.com/1WFT28g9)
bash /path/to/script

---

### Post by Douglas_H_Campbell on 2014-12-02
[**Bug 87771**]("https://bugzilla.kernel.org/show_bug.cgi?id=87771") - No sound in Linux after rebooting from Windows. Gigabyte GA-Z97-D3H motherboard.  
 

 [TABLE]
[TR]
[TH]             [Status]("https://bugzilla.kernel.org/page.cgi?id=fields.html#bug_status"):                         [/TH]
[TD]             RESOLVED CODE_FIX              [/TD]
[/TR]
[/TABLE]
 

   _Here's the fix which I am trying to understand and apply._
 

 OK, then try to install hda-verb program
(included in the latest alsa-tools package), and run like below as
root on the non-working system: 

    hda-verb /dev/snd/hwC0D2 0x20 SET_COEF_INDEX 0x07
     hda-verb /dev/snd/hwC0D2 0x20 SET_PROC_COEF 0x7cb0 [B]

ANSWER[/B]

 

root@meklon-desktop:/home/meklon# hda-verb /dev/snd/hwC0D2 0x20 SET_COEF_INDEX 0x07
 nid = 0x20, verb = 0x500, param = 0x7 
value = 0x0 
root@meklon-desktop:/home/meklon# hda-verb /dev/snd/hwC0D2 0x20 SET_PROC_COEF 0x7cb0
 nid = 0x20, verb = 0x400, param = 0x7cb0 value = 0x0 

Some kind of black magic for me) Sound appears after this. 

**REPLY**

 Thank you for your attention. The bug is not
critical. The can be a workaround with adding the script during the
system startup.

 hda-verb /dev/snd/hwC0D2 0x20 SET_COEF_INDEX 0x07
 hda-verb /dev/snd/hwC0D2 0x20 SET_PROC_COEF 0x7cb0

---

