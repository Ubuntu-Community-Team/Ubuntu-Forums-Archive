---
title: "Problems with GRUB after copying Ubuntu 7.10 drive image back to hard drive."
date: 2008-04-11
forum: General Help
---

### Post by 0graham0 on 2008-04-11
Hello,

I recently imaged the SATA hard drive of an Asus F3sv, which was running Ubuntu 7.10 for amd64. When imaging I kept all the partitions intact. After copying the image back to a clean drive, I attempted to boot the computer and was greeted by a black screen with "GRUB" and a blinking cursor.

I then booted the computer from the ubuntu alternate install CD, and reinstalled the grub bootloader to /dev/sda1

Still, I am greeted by the same boot screen (GRUB and a blinking cursor).

Any help is greatly appreciated, thanks...

---

### Post by ibuclaw on 2008-04-11
Is the file **/boot/grub/menu.lst** correct?

It is instructing GRUB to look in the right location on the right drive?

If you are not sure, load up your Linux LiveCD and type in this command in the terminal.
```
 sudo fdisk -l 
```
Copy & Paste the output into a new post.

Then, mount your partition, and **chroot** your mounted partition to "/"
```
 sudo chroot /media/sda1 
```
(Your harddrive may not have the same  name, or be in the same location, change it accordingly).

Then open up **/boot/grub/menu.lst** with a text editor and Copy & Paste everything from
```
 ## ## End Default Options ## 
```
to
```
 ### END DEBIAN AUTOMAGIC KERNELS LIST 
```

Regards
Iain

---

### Post by 0graham0 on 2008-04-11
I tried pointing grub to each partition on the drive with no luck. I have actually conceded defeat and gone ahead with a clean install, but thanks for the advice.

---

### Post by ibuclaw on 2008-04-11
As long as no important data was lost. I'll accept your actions as being very wise.

Though, regardless of what you were doing. Two very important pieces of advice are to:
```

**A)**  Use a separate partition for **/home**. That way no user data is lost.

**B)**  Backup your currently installed programs using:
**dpkg --get-selections | awk '{if ($2="install") print $1" "}' | tr -d '\n' > instpackages**
When done with the install and you boot into a clean system, use:
**sudo apt-get install `cat instpackages`**

**B2)**  If you are upgrading to a new distribution, then alot of the package 
names will have changed or become redundant or as part of another package. 
Thus the above way would produce alot of errors.
So an alternate way would be just to take a note of all important programs that
you use from the main menu and terminal. And install them manually.
Then all excess dependancies that you don't take note of will come along with them.

```

Regards
Iain

---

### Post by 0graham0 on 2008-04-11
Well, I went ahead with the clean install and more posts and decided to write the image to the drive again and try out your advice.

However, the drive works perfectly! I was using Norton Ghost 11 off of Hirem's Boot CD for the record. The first time I transferred the image back to the drive I ran into grub problems. I wiped the drive clean and transferred the image again and now it works perfectly. Thanks for all the helpful posts...

---

