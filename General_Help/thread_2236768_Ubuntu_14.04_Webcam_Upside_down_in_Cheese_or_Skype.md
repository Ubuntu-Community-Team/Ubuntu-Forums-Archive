---
title: "Ubuntu 14.04 Webcam Upside down in Cheese or Skype on Asus Pro31F Laptop"
date: 2014-07-28
forum: General Help
---

### Post by Smokin Whale on 2014-07-28
Hey guys,

Getting a weird problem on my Grandma's laptop here. After upgrading from Ubuntu 12.04 to Ubuntu Gnome 14.04, I've noticed her webcam is now flipped upside down. This happens in both Cheese and in Skype. Camera was working perfectly fine in Ubuntu 12.04 without it looking like I'm hanging from the roof. I did a little reading and found some skype related issues but I'm having problems in both cheese and skype so I'm not too sure where to go from here.

Any advice would be greatly appreciated, thanks in advance.

---

### Post by Smokin Whale on 2015-01-14
Never solved this, replaced laptop and installed Windows on it for new owner. Maybe one day it'll get solved through a software update.

---

### Post by Roxana_Bestrin_Fue on 2015-10-28
I finally fioud a solution to this problem after a seemingly endless search. Try the simple steps below, taken from [https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)
 Good luck!

**3. Picture is upside down or mirrored**

 
[LIST=1]
[*]Check if v4l2ucp is installed by opening terminal an running the command: apt-cache policy v4l2ucp
[*]Install v4l2ucp by running the command: sudo apt-get install v4l2ucp
[*]Open "Preferences" and "[Video4Linux]("https://help.ubuntu.com/community/Video4Linux") control Panel"
[*]Check/uncheck Flip options
[/LIST]

My Asus laptop actually indicated Video4Linux was alreay installed but because I couldn't find it in Preferences, I installed it anyway, and of course the rest of the steps where easy enough to follow and worked perfectly.

---

