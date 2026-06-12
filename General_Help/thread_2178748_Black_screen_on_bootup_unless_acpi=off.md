---
title: "Black screen on bootup unless acpi=off"
date: 2013-10-05
forum: General Help
---

### Post by lama2p0 on 2013-10-05
[B]2 possible solutions if you have this or similar problem.
First fix is on 2nd post.
Second fix is here: [/B][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150)

I had this working after running updates with acpi off, but now after more updates this is an issue again.. Some help greatly appreciated.
I would hear the bongos that play when the login screen appears, but the screen would be black.

Ubuntu 13.04
My laptop is Toshiba Satellite U305-S5097

Did not see any acpi settings in BIOS, not very many settings at all actually..


acpi seems like it might not be related. As with the fix, during reboot often still get black screen.. Occasionally it goes through without a problem, but it takes a series of reboots to do so.
Please help.

New thread for my issue: [http://ubuntuforums.org/showthread.php?t=2178963&p=12808590](http://ubuntuforums.org/showthread.php?t=2178963&p=12808590)

---

### Post by lama2p0 on 2013-10-05
Solved.
Solution is;
```
sudo nano /etc/default/grub
```
Edit this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
To look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```
Save the edit.
```
sudo update-grub
sudo reboot
```

---

### Post by Bucky Ball on 2013-10-05
Good work and took the words right out of my keyboard. ;)

---

### Post by olipoh1 on 2013-10-05
Hello,

it didn't work for me :-(... well, only once.

I opened a new thread : [http://ubuntuforums.org/showthread.php?t=2178836](http://ubuntuforums.org/showthread.php?t=2178836) with more information on my error.
Thank you.

---

### Post by lama2p0 on 2013-10-05
Not solved. acpi seems unrelated to my problem now. Edited first post.

---

### Post by Bucky Ball on 2013-10-05
You would be best to start a new thread as the title of this one won't reflect your new issue, whatever that is. Cheers. ;)

---

