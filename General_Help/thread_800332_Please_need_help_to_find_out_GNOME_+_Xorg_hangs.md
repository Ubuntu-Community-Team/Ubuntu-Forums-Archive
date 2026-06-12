---
title: "Please need help to find out GNOME + Xorg hangs"
date: 2008-05-19
forum: General Help
---

### Post by rainefan on 2008-05-19
Hi ppl! Since I'm unable to catch this nasty problem on my machine running HardyHeron, I'm posting here too see if you can help me on finding out what it's hanging my GNOME + Xorg session, even mouse + keyboard has no response ](*,) :frown:

This could be a hardware problem, but no kernel screen of death has happened, even no error logs.

Please give me some advices and tricks to where start from, to find out this hanging thing :(

Thnx!

regards,
Raine

BTW: Some info:
Linux ejuan-linux 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

System is up-to-date also.

Recently I have changed from a Dell optiplex 740 with AMD 4200+ to another optiplex 740 but with AMD 4400+ processor intead. Same hardisks, same bios config and same linux install from older hardware. Could thius be a problem? I use NVIDIA proprietary drivers. And it's working right now.

---

### Post by ibuclaw on 2008-05-19
If the system hangs to the point where using "**Ctrl+Alt+Backspace**" doesn't free you from it, then you are experiencing a serious hardware hang.

First, I'd recommend that you remove both "hardy-proposed" and "hardy-backports" from your repository sources, and then downgrade back to the 2.6.24-16 kernel.

Secondly, is this happening after a certain device performs a certain task? (ie: your system hangs when you connect to your wireless router.)
Or just on random occasions?

Also, what is the model of your Motherboard?

Regards
Iain

---

### Post by rainefan on 2008-06-03
Hi Iain! Thanks for your help. Actually my system is a Dell Optiplex 740. After a lot of reinstalling Ubuntu, changing harddisk etc, I finally opted to upgrade my bios version to 2.1.6. In the same day some Xorg updates were also installed. Since then, 2 weeks or so, never had the problem again! I also posted in launchpad this strange behavior.

I really don't know who's fault was, but, what I can guarantee, is that my system still works very well. I would advice people upgrading their bios if possible, in the first place before trying any other solution.

Sorry for posting late, but I thought that this post was deleted from the forums...

Thanks for you help and attention!
Regards,
Raine

---

