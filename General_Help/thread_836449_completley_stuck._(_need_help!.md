---
title: "completley stuck. :( need help!"
date: 2008-06-21
forum: General Help
---

### Post by boyce1 on 2008-06-21
OK, my computer is crippled. 

To keep it short, i was dual booting ubuntu 8.04 with windows xp sp3, and it was all fine.

i previously had some trouble getting grub after installing windows, (it came up with an error whilst trying to install from a livecd). however, i got grub eventually from an alternative cd and the rescue option.

Now, yesterday my Windoze was playing up, it constantly rebooted at startup. I couldn't access any files from it, as it had to be 'cleanly' shut down to allow access from linux.

I put in the windows cd, and tried to repair it, i ran chkdsk /r from the cmd console there and it eventually said that it repaired some errors. however, i booted back up to be rebooted once again.

ok, so i kinda accepted my windows is screwed.

however, grub is gone, and i can't get it back. from a livecd the sudo grub... method doesnt work, and i when i try to install it from the rescue disk it comes up with a fatal error, and can't install grub. 

i also tried to see my partitions through gparted, but it  comes up with 242gb of unallocated space :(


i honeslty don't know what to do. at the moment, all i can do is watch my windoze loop with rebooting... :(

please, does anyone know what i could do? if there was any way for me to access the windows partition, and reinstall grub it would be extremely helpful. thanks.

---

### Post by Aaron_Griffiths_92 on 2008-06-21
Re install the whole system, 1 thing you could do if you wanted to keep your files would be to install over the xp partition and specify that you do not want to overwrite any data, your program files will not work, but you will be able to grab spare files you need before formatting ;)

---

### Post by boyce1 on 2008-06-21
well, ive somehow managed to make a directory and access the windows files... weird...

but any idea how i could install grub?

---

### Post by MagicMoonLight on 2008-06-21
Hey Maybe I can help it sounds like your grub needs to be reinitialized.

Ok if not see grub startup when the computer starts up then possible windows rewrote your Master Boot Record cause grub to no longer start.

Don't worry this is an easy fix go to this link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub) 

I hope this helps you also about windows rebooting that sounds like something went wrong with windows but that could be many things in windows causing that .

Thats why I don't use windows much often anymore to many things can go wrong with it.:lolflag:

Good Luck

---

### Post by boyce1 on 2008-06-21
i've already tried that, 

after grub> setup (hd0), i get an error message (error 12) saying that it didn't install.

---

