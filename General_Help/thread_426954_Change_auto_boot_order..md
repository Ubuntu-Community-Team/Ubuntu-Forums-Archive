---
title: "Change auto boot order."
date: 2007-04-29
forum: General Help
---

### Post by Rictus on 2007-04-29
I have Fiesty and XP installed on seperate disks. I like to leave it boot on the Ubuntu disk but have it automatically list windows first so if it reboots it will load window but if I select Ubuntu it will load that. I've done this along time ago in breezy but don't remeber how to change the list priority.
Thanks,
Rick

---

### Post by Emerzen on 2007-04-29
Here's a GUI startup manager for Feisty, works like a charm and configurable.

[http://web.telia.com/~u88005282/sum/installation.html](http://web.telia.com/~u88005282/sum/installation.html)

---

### Post by Rictus on 2007-04-29
No offense but I'm pretty sure it's just a small adjustment and I don't really want to try and install something that the first thing it say on the page is:

***WARNING***
If you are unlucky, this tool could make your system unable to start. USE IT ON YOUR OWN RISK!

---

### Post by Bigbluecat on 2007-04-29
You need to edit the menu.lst fie. It is located in /boot/grub

Once there make a backup:

sudo cp menu.lst menu.lsy_backup

Then edit the file:

gksudo gedit menu.lst

You are looking for the line that says ## default num. At the bottom of this little section there is a default setting option.

Set default to the number of the OS that you wish to boot by default. Remember that grub starts counting from zero so count down the order of kernels and insert the number as appropriate.

For example:
default        3

Would set the 4 entry as the default boot.

I also find it useful to set updatedefualtentry=true

This way the number you have set for default is updated if you get a kernel upgrade and it is inserted above your default OS.

Save and you are done.

---

### Post by Tomosaur on 2007-04-29
You could take a look at the link in my sig, which will allow you to do what you're trying to do very easily, by simply changing the default boot. It can do some other Grub-related stuff which you may be interested in, too.

However - editing the /boot/grub/menu.lst file is pretty straightforward in itself, you can just follow Bigbluecat's instructions if you feel like.

---

### Post by Rictus on 2007-04-29
OK thanks you guys.

---

### Post by Andyroo on 2007-04-29
Just a quick question, I'm a new Ubuntu user so bear with me :D

I'm in the same situation with the boot order, however i have put Ubuntu onto a second hard disk separate from windows.  This means that both OS's are listed at position 0 in the menu.lst file.  Although windows is hd0,0 and Ubuntu hd1,0.

is it just a case of putting hd0,0 as default? I dont want to change anything in case my machine refuses to boot completely!

heres part of my menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5a09a965-409b-42c7-a72c-afcddc5d5d16 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5a09a965-409b-42c7-a72c-afcddc5d5d16 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Tomosaur on 2007-04-29
If you have made any changes to your physical machine (ie, swapping hard drives etc), then the simplest solution to ensure that grub is configured correctly, is to open up a terminal and type the following commands:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo update-grub

```

The first command backs up your current grub configuration, while the second command forces grub to rescan your system and alter the configuration file accordingly. It should detect your new drive arrangement and set itself up accordingly. You can then modify your grub preferences as you would normally.

---

### Post by Andyroo on 2007-04-29
I apologize I should have made myself much clearer.  What I meant was that i wanted to make Windows XP the default selection in grub.  If ubuntu was on the same hard drive Id have no problem, but since they are on different physical drives Im not so sure.

---

### Post by Bigbluecat on 2007-04-29
Andyroo

Your windows number is 2

Your main Ubunutu would be 0
Ubuntu recovery mode would be 1
Windows is 2

Grub is counting the order in the menu.lst file - not the order on each disk.

---

### Post by Andyroo on 2007-04-29
Ah! I see, thank you very much! :)

---

