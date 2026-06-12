---
title: "Can't fix messed up GRUB2 config"
date: 2020-05-23
forum: General Help
---

### Post by csg2 on 2020-05-23
I have Ubuntu installed on a laptop. Sometimes when the laptop goes to sleep, I can't get it to wake up. The only thing I have figured out to do in these cases is cycle power. (I know this isn't a particularly good idea.)

The last time I did this, the system did not boot. Instead the GRUB prompt came up. I looked up how to boot in this case and was able to do so. The final instructions for that said that to fix the GRUB configuration you needed to run update-grub and then grub-install. So I did this and then rebooted. 

It got worse. I got the grub rescue prompt. So I looked up what to do then. Apparently some of the GRUB mods were corrupt and I could not boot this way. 

I used the Ubuntu live-cd and from a terminal there ran grub-install. This got me back to the point where I could get the regular grub prompt and load the kernel and initrd from there. 

From the live cd I ran an fsck with the -c option to mark bad blocks. I then went back to the OS on the laptop and tried update-grub and grub-install again. Now I don't get a grub prompt at all. Instead I get a boot loop where grub shows me a menu and then can't load the OS and then the menu and on and on. 

I haven't tried doing a grub-install from the live cd again. 

Any ideas? 

Thanks!

---

### Post by csg2 on 2020-05-24
I went back and used the live CD to do grub-install one last time. Now it works. I can only assume that fsck fixed some bad blocks and it took a couple of tries to restore the files.

---

