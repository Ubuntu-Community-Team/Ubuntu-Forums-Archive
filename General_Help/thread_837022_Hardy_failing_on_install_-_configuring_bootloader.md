---
title: "Hardy failing on install - configuring bootloader"
date: 2008-06-22
forum: General Help
---

### Post by psylo on 2008-06-22
Hi all,

I've put 8.04 on several machines now so this is a bit of a weird one. I'm taking an old windows workstation and want to rebuild it into a test machine. 

I've run the Live-CD to check hardware etc and it all seems to operate okay but when I go to install *every* time it gets to 94% and goes to configure the bootloader (GRUB) it hangs. 

It's not the heftiest machine so I decided to leave it for a while the last time however after 3 hours it was still sitting there at 94% at which point I killed the process and rebooted.

Upon reboot I get a GRUB error Code 15 which to my knowledge is where it can't find the kernal to load.

So my questions are:

1. Will the kernal be there to be loaded and it's just the boot config file need editing? If not, how do I install a kernal to be able to boot from?

2. If it's just a GRUB misconfig can I mount the HDD from the Live CD and edit the file and tell it where to find things? If so how do I do this?

I'm quite happy playing around with Ubuntu when I'm actually up to the point of having an OS but beyond making an edit to the Listing file for GRUB I'm quite lost at this end.

Any thoughts, comments, options would be greatly appreciated.

Cheers
AndrewF

---

### Post by psylo on 2008-06-22
bounce.

---

### Post by chrissy833 on 2008-09-15
I have exactly the same problem.  I also tried installing with a new hard drive and it didn't work.  I attempted to install Kubuntu and Ubuntu and I have no idea what to do next.

---

### Post by caljohnsmith on 2008-09-15
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=810205&highlight=circumvented+ext2+ext3](http://ubuntuforums.org/showthread.php?t=810205&highlight=circumvented+ext2+ext3)

Let me know how it goes. :)

---

