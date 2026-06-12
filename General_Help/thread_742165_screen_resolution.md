---
title: "screen resolution"
date: 2008-04-01
forum: General Help
---

### Post by Aat on 2008-04-01
I have a monitor with a maximum resolution of 1280x1024, but I discovered it can also display 1400x1050. So I made this my standard setting.
But once in a while when I log in it sets the resolution at 1024x768. I then have to manually put it back at 1400x1050. This won't take effect until I have logged out and logged in again.

This doesn't happen all the time though, it's as if my computer randomly decides when to let me use max resolution. It's not the end of the world, but it is becoming annoying.

Can anyone tell me where ubuntu stores the default setting for screen resolution? I checked xorg.conf, but it seems OK, with 1400x1050 selected as standard.

Thanks in advance.

---

### Post by Arwen on 2008-04-01
Hello!
I can't actually help you,I don't know much about this but I think you could try to change xorg.conf for both your account and the root's account.I once (in pclinuxos) deleted a resolution that exists in xorg.conf and replace it by the one you want(and put it in the beginning of the line).I don't know if this works in ubuntu but I have strange experiences with xorg.conf.

Good luck!

---

### Post by Aat on 2008-04-01
Thanks for the help. But I wasn't aware that there are multiple versions of xorg.conf for multiple users. I just looked in /etc/X11/xorg.conf. I assume this is the file for the root user. Can you tell me where I can find the files for the different users?

---

