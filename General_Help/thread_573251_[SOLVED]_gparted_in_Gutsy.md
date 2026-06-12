---
title: "[SOLVED] gparted in Gutsy"
date: 2007-10-11
forum: General Help
---

### Post by ronmarley1 on 2007-10-11
When I launch gparted, it starts, the slider at the bottom moves back and for, the hard drive is cranking, but gparted never displays any information in the window.  Even after closing gparted, the hard drive continues to spin.  Eventually, it does stop spinning.
Any insight here would be appreciated, thanks.
PS, nothing exotic here, just an IBM R51 Thinkpad that dual boots XP and Ubuntu.

---

### Post by dabl on 2007-10-11
I like booting a GParted Live CD and using it that way better than running it from *buntu.  For one thing, it's a more recent version of the program.  Download the ISO and burn it to make your own live CD:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

:guitar:

---

### Post by strabes on 2007-10-11
You can't edit partitions while they're mounted. In order to resize or change partitions you have to be in a live CD environment. The best option at the moment is a gparted live CD.

---

### Post by fjgaude on 2007-10-11
I've not had trouble changing drive partitions on the same system, but not the one that booted the system. I have an eight-drive system and can use Gparted to work on drives that are unmounted, without using a liveCD.

If you have only a one-drive system, do as dabl suggests.

---

### Post by ronmarley1 on 2007-10-12
Thanks for the replies.  I should've been clearer in my original post.  Actually, I really wasn't trying to use gparted to change partitions, I was just testing the different apps on Gutsy beta and that was the only one not working for me.  Previously, I was able to run gparted and view the partition info.  It does not that for me now.  I just used to use it to show partition info. to my high school students that were interested in trying Ubuntu.  No big deal really, just curious.  I'll use the live CD to do that.
Have a nice weekend everyone!  Go Indians!

---

### Post by ronmarley1 on 2007-10-12
Issue solved.  I just started gparted and went and took a shower and when I came back, the partition info. was displayed.  Looks like it just took a while.  I should've been more patient.
Thanks for the replies!

---

