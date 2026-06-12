---
title: "Linux Boot Problem"
date: 2007-04-13
forum: General Help
---

### Post by Zarathu on 2007-04-13
I had Windows and Linux on my hard drive; everything was going great.

Before:
Windows - (hd0,0)
Linux - (hd0,1)

Then, I installed Mac, but I moved Linux to (hd0,2) and Mac to (hd0,1).  Mac overwrote GRUB, so I threw in the Live CD and reinstalled GRUB, which wasn't a problem.  However, GRUB is now giving me a problem:

[http://img110.imageshack.us/img110/3329/40600139yf4.jpg](http://img110.imageshack.us/img110/3329/40600139yf4.jpg)

Also, I didn't forget to edit the line in GRUB to make it root (hd0,2) instead of (hd0,1) like it had before.  Note:  I used an Ubuntu 6.10 CD to reinstall GRUB, but I have Ubuntu 6.06.  That shouldn't be a problem, right?  My friend is borrowing my 6.06 CD.

---

### Post by Zarathu on 2007-04-13
bumper?

---

### Post by Zarathu on 2007-04-13
I had Windows and Linux on my hard drive; everything was going great.

Before:
Windows - (hd0,0)
Linux - (hd0,1)

Then, I installed Mac, but I moved Linux to (hd0,2) and Mac to (hd0,1). Mac overwrote GRUB, so I threw in the Live CD and reinstalled GRUB, which wasn't a problem. However, GRUB is now giving me a problem:

[http://img110.imageshack.us/img110/3329/40600139yf4.jpg](http://img110.imageshack.us/img110/3329/40600139yf4.jpg)

Also, I didn't forget to edit the line in GRUB to make it root (hd0,2) instead of (hd0,1) like it had before. Note: I used an Ubuntu 6.10 CD to reinstall GRUB, but I have Ubuntu 6.06. That shouldn't be a problem, right? My friend is borrowing my 6.06 CD.

---

### Post by NICU on 2007-04-13
Hi, I don't know the changes in GRUB from 6.06 to 6.10, but that shouldn't affect anything, so using the 6.10 CD should be fine. 

I like this article - [http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp](http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp) - for dual booting.  It goes through all the important steps for setting up your partitions.  If you can run your LiveCD again and use GParted (Gnome Partition Editor) and let me know what partitions you have each OS on I can help you figure out your GRUB lists.

---

### Post by ajgreeny on 2007-04-13
So, you're triple booting now?  Or did you replace windows with mac?  Are you sure you got the partitions correct?
win on hd0,0
mac on hd0,1
linux on hd0,2
Is that right?  Gparted mentioned by NICU should give us a clue as to what is going on here.

---

### Post by mhansen on 2007-04-13
What did you do exactly?  Did you add another partition and install the Mac OS on it?  Unless your partition table changed changing the config like you describe would definitely break things...

Can you do an fdisk on that drive, print the partition table, and paste the results?  Thanks.



Regards,
Mike


EDIT: Sorry...this thread went from 0 replies to 3 in the time I posted.  I don't want to sound like I'm repeating anything, or worse, confuse you more...  Carry on.  :)

---

