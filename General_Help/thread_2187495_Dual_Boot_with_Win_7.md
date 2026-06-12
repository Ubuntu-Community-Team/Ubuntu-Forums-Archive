---
title: "Dual Boot with Win 7"
date: 2013-11-12
forum: General Help
---

### Post by davidafranklin on 2013-11-12
Hello,

I just installed Ubuntu 13.10 in dual boot with Win 7. Win 7 was already installed so I installed Ubuntu along with Win 7 from a USB.

Now, when I boot my computer, it does not ask me what OS to chose, it goes directly to Ubuntu.

Is there anything I need to change in the BIOS or within Ubuntu so I can get a screen where I can select the OS?

Thank you

---

### Post by Impavidus on 2013-11-12
Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Post the link to the summary here.

Edit: Usually Mark Phelps's solution works. If it doesn't, try mine. It should tell us what's really going on.

---

### Post by Mark Phelps on 2013-11-12
> Is there anything I need to change in the BIOS or within Ubuntu so I can get a screen where I can select the OS?


All you should really need to do is boot into Ubuntu, open a terminal, and enter "sudo update-grub".  That will regenerate the default GRUB config file and should add an entry for the Windows boot loader.

---

### Post by davidafranklin on 2013-11-12
> **Impavidus said:**
> Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Post the link to the summary here.

Edit: Usually Mark Phelps's solution works. If it doesn't, try mine. It should tell us what's really going on.


I did this and seem to work. I did ths from Ubuntu instead of live CD, is this an issue?
I then did a reboot and after the BIos scren, I get a black screen for about 30s then it loads Ubuntu. Still no choice to Windows.
Any other sggestion?

Thanks

---

### Post by Impavidus on 2013-11-12
Do you have a link to the boot info summary?

---

### Post by davidafranklin on 2013-11-12
not sure what you mean? Could you please detail?

I redid the whle thing from LIve Cd, nothing changed.

I woder if I should do "repair files" in the advanced Menu but I am afraid messing everything up

---

### Post by davidafranklin on 2013-11-12
thiis is maybe what you were referring to:

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/6408256/](http://paste.ubuntu.com/6408256/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.

---

### Post by oldfred on 2013-11-12
Boot-Repair runs the sudo update-grub command.

It show that the grub menu will have these entries:

> Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2

---

### Post by davidafranklin on 2013-11-12
Thanks but not sure what you suggest me to do at this point.

---

### Post by oldfred on 2013-11-12
Are not the menu entries in your grub menu when you reboot?

---

### Post by davidafranklin on 2013-11-13
Still same issue. I have recorded in a video of what happens, see [here]("http://s155643733.onlinehome.us/Misc/WP_20131113_002.mp4"). It is about 1 mn long. You will see after the Bios screen a black screen until second 48. No OS selection option.

Thanks

---

### Post by oldfred on 2013-11-13
Do you get menu with shift key, some UEFI only work with escape key?

It may be the video mode that grub is defaulting to. It now tries to use system video mode.

 gksudo gedit /etc/default/grub

 sudo update-grub


Change this setting:
You can uncomment this line (remove #) and force minimum.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[COLOR=#ff0000]#[/COLOR]GRUB_GFXMODE=640x480


When booting if you do get grub menu you can run from grub command line the vbeinfo to see what modes other than 640x480 your system supports.

---

### Post by davidafranklin on 2013-11-13
i remove he section mentioned below and sill nothing happens during boot, no Menu.
Any other suggestions? Reinstall Ubuntu maybe?
I cannot ever repair Windows as when instalg the CD I can only reinstall
Thanks

---

### Post by oldfred on 2013-11-13
You did not remove entire section did you? Just the [COLOR=#ff0000]#[/COLOR] to uncomment the one line.

---

### Post by davidafranklin on 2013-11-14
Yeap, I removed everything and messed up Ubuntu...
I have reinstalled yesterday Win 7 on its partition and will install tonight Lubuntu instead of Ubuntu.
Hopefully  will not get the same issues.
Will keep you posted.
Thanks

---

### Post by davidafranklin on 2013-11-15
I reinstalled all Win 7 and then installed Lubuntu 13.10 instead of Ubuntu. So now I get the Grub when I boot but no Win7.
I ran again the few cmmand you suggested (boot repair, grub update.. but it did not change anything. I cannot get the last set of cmands with x where i previoulsy deleted everything.
Any other suggestions?
Thanks

---

### Post by davidafranklin on 2013-11-15
I think I might have deleted WIndows 7 when I installed Lubuntu messing up the partition as it could not install the previous Ubuntu.
I checked on Gparted and I cannot see any NTFS partition and the main ext4 partition is the size of my drive so win & is clearly gone.

Any special instructions on how to reinstall WIn 7 and then Lubuntu so that all gets instaled correctly from the start?

---

### Post by oldfred on 2013-11-15
Still do not know why you had issues.

But for Windows to reinstall you have to delete the Linux partition(s). Windows does not correctly see Linux formated partitions. It will want to install into unallocated space or NTFS partition with the boot flag. It must have available primary partition as all Windows boot files must be in a primary partition.

---

### Post by davidafranklin on 2013-11-16
I reformatted everything, re-installed Win 7 then Lubuntu 13.10. At first, I could not chose Lubuntu at boot. Did a boot repair then finally got the boot menu.
However I see 2 windows sd1 and sd2. Is this normal? Is this because there is a small partition or System restore an then the main partition? I seems that it boots from either partition.

If everything stays the same, I am fine but I am afraid that down the road I might face some similar issues especially when I will upgrade later to Lubuntu 14.04. At that time, will it be better to do the upgrade of another fresh install?

Thanks again for all the help

---

