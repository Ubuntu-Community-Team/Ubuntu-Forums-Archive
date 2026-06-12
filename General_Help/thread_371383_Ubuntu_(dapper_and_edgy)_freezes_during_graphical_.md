---
title: "Ubuntu (dapper and edgy) freezes during graphical install and when Gnome starts."
date: 2007-02-26
forum: General Help
---

### Post by ububug on 2007-02-26
I have been able to run Debian Etch (testing) without problems. The other day I was going to reinstall everything so I burned a new cd with the i386 netinstall iso from [http://www.debian.org/devel/debian-installer/index.en.html](http://www.debian.org/devel/debian-installer/index.en.html) but when it came to formatting the partitions it froze so I tried my Dapper Drake cd that I had ordered. It froze right away, fail-safe froze too. 

I burned Edgy Eft and tried that, still no luck. Then I tried with Edgy Eft alternate install (text that is) and got it installed. However, when Gnome started it was frozen before I could login. I restarted and was able to start downloading updates, when it froze again. And that's it, it just keeps freezing and I have to turn the computer off, nothing else works.

Motherboard: EPoX EP-8KDA3+

CPU: AMD Athlon 64 3400+ 2.4 GHz

Graphics card: PowerColor Radeon 9800 PRO 128MB DDR AGP


Any ideas on what I can do to solve this?

---

### Post by cronholio on 2007-02-27
Are there any errors in /var/log/Xorg.0.log (lines starting with "(EE)")?

---

### Post by ububug on 2007-02-28
When I reinstalled Edgy (text install) just now, everything seemed to work just fine, I surfed around with Firefox for maybe 4 minutes and thought that it had just fixed itself somehow, I click the updates button and after downloading two packages I get hard freeze and have to turn the computer off and on again. Fail safe and:

(EE) xf86OpenSerial: Cannot open device /dev/wacom 
no such file or directory.
Error opening /dev/wacom : Success

I get this about 6 times in the end of /var/log/Xorg.0.log Wacom is apparently "the leading manufacturer of pen tablets and pens" but I don't have a pen tablet, so this shouldn't really be it, right? No other (EE)'s there.

---

### Post by cronholio on 2007-02-28
Don't worry about the wacom messages, I think everybody gets those (everybody without a Wacom tablet that is). Is your system running fine now?

---

### Post by ububug on 2007-02-28
No, it still freezes. I played some tetris, surfed around with Firefox, opened and closed OpenOffice, no freeze. When I click the update button and choose to start downloading the 131 packages it freezes right away. I restart the computer and open Firefox to find the command for updating ("apt-get update" and "apt-get upgrade") and everything freezes again, this time without trying to update, just using Firefox. 

Fail safe. I upgrade with the commands and start Ubuntu again, see that I have 5 new packages (linux-headers-generic and linux-image-generic), try to update, freeze again. Try to update in failsafe with commands, but it says that it "kept back" those packages.

---

### Post by ububug on 2007-03-01
Seems like I solved it! I installed the latest BIOS for my motherboard and so far not a single crash!

Thank you cronholio for trying to help me.

---

