---
title: "how exactly does wubi work?"
date: 2008-05-01
forum: General Help
---

### Post by JokerX on 2008-05-01
ive read about it but i have no idea what it is or how it works. is it like a virtual machine? is it emulation? does it kill off my windows stuff? im confused....

---

### Post by chewearn on 2008-05-01
Here you go:
[http://wubi-installer.org/](http://wubi-installer.org/)

FAQ:
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by JokerX on 2008-05-01
thanks!

---

### Post by OMA2k on 2008-05-01
Wubi is NOT a virtual machine. It's an installer that installs a full Ubuntu installation inside an image file, which is, so to speak, a "virtual partition" stored in your regular Windows NTFS partition. But the OS runs independent to Windows, just like if it were installed in a dedicated partition (Wubi adds an option to start Ubuntu in the regular Windows bootloader menu). So it's not a virtual machine for Windows and not an "emulation", like you say; it's just another way to install and boot Ubuntu without partitioning. And of course, it won't kill your Windows installation. It's just installed in a folder like any other program, so you can uninstall it whenever you wish from Windows' "add/remove programs" tool.

---

### Post by darco on 2008-05-01
Wubi's awesome!!...I took off the training wheels on my laptop and now its has its own partition. It was a great ride!...I still have my main pc under Wubi and will move to a partition once LVPM is updated...a little nervous there though. My main pc has all the bells and whistles and I would hate to lose it...:(
Go for it, you wont regret it (make sure you defrag your drive first!!)

darco

---

### Post by OMA2k on 2008-05-01
What's supposed to happen if you don't defrag? One of the Wubi installations I performed was in a big 200 GB partition that only had 20 GB free and hadn't never been defragged after two years! (it was just a test installation). But it works flawlessly so far.

---

### Post by NightwishFan on 2008-05-01
I agree wubi owns. It is excellent for installing on a PC temporarily. I had a school computer I installed it on since I hated the xp and the schools pre-installed crapware.

---

### Post by ago on 2008-05-02
> **OMA2k said:**
> What's supposed to happen if you don't defrag?

If the swap.disk file happens to be very fragmented you might have an error ([https://bugs.launchpad.net/wubi/+bug/222546](https://bugs.launchpad.net/wubi/+bug/222546)). Other than that it is mostly a performance issue. Of course on Windows, running chkdsk /r and defragmenting once in a while is a good idea anyway, whether you use wubi or not.

---

