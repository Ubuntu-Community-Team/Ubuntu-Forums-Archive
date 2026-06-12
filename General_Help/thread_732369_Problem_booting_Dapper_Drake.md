---
title: "Problem booting Dapper Drake"
date: 2008-03-22
forum: General Help
---

### Post by LepricahnsGold on 2008-03-22
Forgive me if this has been posted but I couldn't find it.
I have an AMD Athlon 1.1 Ghtz system with 512 MB RAM. It is set for dual boot (Ubuntu and Win XP).
I had some system trouble due to lightning that, as you can see, has been corrected (It had taken out the router, cable modem and NIC card). Here is my trouble. I can boot into Win XP (where I am now) but if I try to get into Ubuntu (Dapper Drake), I see:

Loading essential drivers....                                 OK
Mounting root file system....

and there it stays, never saying OK. Wildest part is it does this whether I try to boot from the hard disk or the CD.  I'm sure this has been encountered before so if someone has a link to the solution, please PM or email it to me. Thanks.

P.S. I'm a noob so keep it simple. :-)

---

### Post by Shazaam on 2008-03-22
Does the cdrom work ok in Windows? Have you tried a different linux livecd?

---

### Post by LepricahnsGold on 2008-03-28
Yes, the CD works in Windows (opens a browser). I have no other livecd, just this one. I find it odd that the HDD and CD copies both went out but far from impossible. I can (and probably will) order a new CD, so I have the latest version of Ubuntu,

---

### Post by LepricahnsGold on 2008-04-18
OK. now I have a new LiveCD of Ubuntu 7.10. When I boot  from this, I get the menu and select to Open Ubuntu. It goes to a screen with a bar an orange area moves back and forth. After about 3-4 passes, it stops and sits there. I can reset my machine but can't gert farther.

---

### Post by Shazaam on 2008-04-18
Try to boot Dapper (if you still have it installed) and choose "Recovery Mode" at the grub screen.

---

### Post by LepricahnsGold on 2008-04-20
OK. I went to the GRUB screen and there were two listings for Ubuntu 6.06. One says 2.6.15-23-386 (the older). In recovery mode, it goes through several lines then stops at:
[17179572.142000] ide 0 at 0x1f0-0x1f7,0x3f6 on irq 14

The other, numbered 2.6.15-51-386, also runs through several lines and stops at:
[17179572.968000] ide 0 at 0x1f0-0x1f7,0x3f6 on irq 14

---

### Post by usien on 2008-04-20
Try checking the disk for defects. How do you write your CD's? Frequently, CD's written at high speeds have defects. If you do find defects, then write the cd at 4x or as low as you can. Hope that helps!
[EDIT: Wrong Reply. Sorry, i didn't understand your problem. Moderators feel free to delete this post.]

---

### Post by Shazaam on 2008-04-20
> **LepricahnsGold said:**
> OK. I went to the GRUB screen and there were two listings for Ubuntu 6.06. One says 2.6.15-23-386 (the older). In recovery mode, it goes through several lines then stops at:
[17179572.142000] ide 0 at 0x1f0-0x1f7,0x3f6 on irq 14

The other, numbered 2.6.15-51-386, also runs through several lines and stops at:
[17179572.968000] ide 0 at 0x1f0-0x1f7,0x3f6 on irq 14

Just a guess but do your cd/dvd-rom drives work ok using Windows? Lightning can play havok with a lot of hardware. Once Windows boots to the desktop insert the Ubuntu disk in the drive(s) and see if the splash screen comes up.

---

### Post by LepricahnsGold on 2008-04-21
Yea, works fine in Windows. I've installed Return to Castle Wolfenstein CD on it.

---

### Post by LepricahnsGold on 2008-05-03
Problem fixed. I got a new computer. :)

---

