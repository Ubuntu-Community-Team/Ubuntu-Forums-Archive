---
title: "[SOLVED] Bootup Details --- Don't Hide it  From Me !!! LOL"
date: 2007-10-22
forum: General Help
---

### Post by nooblot on 2007-10-22
Instead of the pretty UBUNTU logo,
how can I make the system display the gory details at boot-up ?
you know...a la Red Hat

thanks

---

### Post by Arwen on 2007-10-22
Is [this]("http://ubuntuforums.org/showthread.php?t=370149") what you want?

---

### Post by infinito on 2007-10-22
> **nooblot said:**
> Instead of the pretty UBUNTU logo,
how can I make the system display the gory details at boot-up ?
you know...a la Red Hat

thanks

Go to /boot/grub/menu.lst (as root) and in the lines that start with "kernel" remove "quiet splash" and change the lines that have "quiet" alone for "boot"

---

### Post by Lord_Dicranius on 2007-10-22
Or you wanting all the test that shows you what linux is doing during bootup?  If that is the case, install startupmanager from the repositories (search for it using Synaptic or run this from the terminal "sudo ap-get install startupmanager").  You'll see an option for "Startup Manager" in the Control Center now (System>>Preferences>>Control Center - some people don't have the Control Center on that menu, so you may need to edit it and add it).  Open that up and there'll be a check box at the bottom to bootup showing text.

---

### Post by MJN on 2007-10-22
You will need to open up **/boot/grub/menu.lst** in an editor and remove the **quiet splash** options from the **defoptions= **line (leave a space after the =)[1]. This tells grub to not use these options for the default boot option. Make the changes take effect with **sudo update-grub**.
 
If you just edit a particular kernel line then you'll have to redo the change when you update the kernel.
 
If this makes no sense to you just shout and I will add more detail.
 
Mathew
 
Edit: Wow - looks like we all responded at once to this one! Oh well.. take your pick!

[1] There is a bug in grub versions <0.97-19 which causes a non-empty defoptions directive to be taken as missing (and hence ignored). So, to workaround this put a space in after the =. Note however that the subsequent update-grub will remove this space. (To the OP - you should be okay using Feisty - no need for a space)

---

### Post by nooblot on 2007-10-22
ok thanks
will try after I'm done with the upgrade :guitar:

---

