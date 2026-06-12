---
title: "Sorry Ubuntu 14.04 has experienced an internal error"
date: 2014-06-09
forum: General Help
---

### Post by ahounsome on 2014-06-09
Hi Guys,

I have rebuilt my HP 2530p Notebook with the latest Ubuntu build but I'm still getting the same error as detailed below:-

```
Sorry Ubuntu 14.04 has experienced an internal error
Executable path
usr/share/apport/apportcheckresume
```

So the box isn't able to deal with suspend\resume tasks properly. In fact when I close the lid it goes into suspension for a few seconds then gives up and reboots.

Anyone any ideas on fixing this?

---

### Post by Kirboosy on 2014-06-09
From a terminal if you enter the following command does the computer properly suspend?

```
sudo pm-suspend
```

I also came across the post on the forums and I've heard people report success with it working for them.
[SIZE=1]
[/SIZE][h=2][SIZE=1][ 					[SIZE=2][FONT=arial]Ubuntu 12.04 LTS Suspend not working FIX 				[/FONT][/SIZE]]("http://ubuntuforums.org/showthread.php?t=1978290&p=11926504")[/SIZE][/h]Hopefully its as easy and simple for you! Let me know if that doesn't work.

Hope that helps!
~Caboose

---

### Post by ahounsome on 2014-06-09
hmmmm, many thanks for your help on this. Unfortunately this didn't work. It actually has disabled the suspend feature all together now! Any other thoughts?

---

