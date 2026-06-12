---
title: "Reinstall grub help"
date: 2007-05-25
forum: General Help
---

### Post by telovoyagarcar on 2007-05-25
I just reinstalled windows XP to my last partition, then fixed the Vista boot loader and now the final step is to reinstall Grub so i can finish setting up my triple boot system. I already had Feisty installed in another partition and the swap space.
I am using the alternate CD in text mode.

I did search the site and found this tutorial:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

im going with the first option, the one where i get to the partitioner step. But here is the problem.
at the 4th step (4. Mount your appropriate linux partions)... i don't have the / (root) option. I get the ext3, ext2, swap and other options but i don't see where is the option to tell the partitioned to use that partition as root?
I know the graphical installation from the normal live cd, has the options to tell what to mount on each of the partitions, but the live cd does not work on my machine.. the only way is with the alternate cd.

So i get an error message telling me that i did not specify the root partition and can't continue.
Remember that i do NOT have to re format the linux partitions as i already had the system set up before... just need to trick the installation so it will re install grub.

Thanks a lot.

---

### Post by merlinus on 2007-05-25
Have you tried this from a terminal:

```

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

Just be sure to substitute your results from find in the next two commands.

Good luck!

-merlin

---

### Post by tokker73 on 2007-08-29
I have the same problem.

Merlin, how do I get to open the terminal and type these commands?
(me too i am using the alternate cd)

---

### Post by merlinus on 2007-08-29
Boot into recovery mode, if that is available on the opening menu. Log in and then press Ctrl-Alt-F1 to get to a command line.

Otherwise, you might try supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

-merlin

---

### Post by bodhi.zazen on 2007-08-30
> **tokker73 said:**
> I have the same problem.

Merlin, how do I get to open the terminal and type these commands?
(me too i am using the alternate cd)

You can do this from the Ubuntu Live CD

---

