---
title: "how do I remove the Beryl Xorg and go back to the original Xorg?"
date: 2006-12-21
forum: General Help
---

### Post by maddbaron on 2006-12-21
installed Beryl never got it work. System response went down, rebooting takes about 5 hard reboots to get system to go past "starting up" after grub. 
I removed Beryl via Adept.
I remember the install instructions saying to create a new xorg file exclusively for Beryl and make system use that.
I believe my system is currently using the Beryl Xorg. I want to go back to my original Xorg since this is slowing down my system performance.
How can I switch back?

---

### Post by hanzomon4 on 2006-12-21
Did you use XGL or AIGLX ? Either way  run this command ```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by maddbaron on 2006-12-21
I used xgl... i think i read to add xserver-xgl. any way of removing that?

thank u

ok I ran that and it reconfig'd. 

I hope this fixes the need to reboot several times just to get kubuntu working.

---

### Post by hanzomon4 on 2006-12-21
You may also need to edit your /etc/gdm/gdm.conf-custom

---

### Post by wpshooter on 2006-12-21
> **maddbaron said:**
> 
How can I switch back?

I have no idea, but let me say that from some of the post I have been seeing on here, I say that it is a pretty good move on your part.

Good luck.

---

