---
title: "GRUB failure"
date: 2007-02-26
forum: General Help
---

### Post by Moses on 2007-02-26
Here's the background information:

I had Ubuntu Ultimate 1.1 and Windows XP succesfully dual booting with GRUB. 
I finally got Beryl running, but soon after encountered some trouble (I'd like to address this problem next), basically, when logging into Ubuntu I would get a blue screen with a curosr for 3 seconds and then the login screen would come up again. This happend with **all** the session types, including failsafe terminal.

At this stage Windows XP was still booting fine. 

In an attempt to fix the Ubuntu problem, I booted into Ubuntu recovery mode, and ran "startx". I then was just looking around, when I came accross the bootup option, and decided to change my timeout from 5 seconds to 3 seconds. I thought this was pretty innocent. 

I then restarted and GRUB wass totally incorrect. XP has disappeared from the list, and there are now 4 Ubuntu boot options, 2 recovery options and 2 normal ones, but none of these actually work. I just get an error (21 I think). I can now only boot with the Ultimate CD, I've been looking around for the boot.lst, but I can't find it.

Any help would be greatly appreciated. Thanks in advace.
Let me know if you need any further details.

---

### Post by cronholio on 2007-02-27
Boot from the Live CD and mount your root partition. The file you are looking for is /boot/grub/menu.lst. Would help if you could post it here.

---

### Post by Moses on 2007-02-27
Yeah I meant menu.lst. My bad. 

I have since fixed the problem, thanks anyway.

---

