---
title: "Grub problem"
date: 2007-06-29
forum: General Help
---

### Post by dondad on 2007-06-29
I am trying to install Fiesty to my second computer. It has two hard drives, one 80 gig drive that has Windows xp, and a second one that is a 250 gig partitioned with a 40 gig ext3 (ubuntu installed here), a 2 gig linux swap, and then the rest as ext3 setup as /home. When I try to boot after the install, I get a grub error 21. I searched and found a couple of threads about this, but the instructions did not fix it. I booted from the live cd, opened a terminal and did the following:

sudo grub to get a grub prompt
find /boot/grub/stage1
**output of this is (hd1,1)
root (hd1,1)
setup (hd0)
exit

From what I can see, this reinstalls grub, but it made no difference. It still gets to stage 1.5 and throws and error 21.Most of the questions I see involve ubuntu installed on a second partition of the first drive. Do I need to do something different because it is on a different drive?

For the time being, I used the windows setup disk to fix the mbr so that I can get the computer up and it boots fine into windows.

What can I do to get grub to work with this configuration?

Thanks for the help.

I fixed it. I happened to notice that the primary controller for the second drive was turned off in the bios. I turned it on, reinstalled grub, and it works.

---

