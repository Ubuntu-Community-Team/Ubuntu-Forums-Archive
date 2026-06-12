---
title: "Extreme Ubuntu Customization"
date: 2006-12-31
forum: General Help
---

### Post by allwin on 2006-12-31
1. I'm not particularly enamored of the Ubuntu brown color scheme.  I've found how to customize the login screen and the desktop, but how does one change the panel that comes up when you log on to Gnome (the panel that says Nautilus etc. is loading), which comes up between the login screen and the desktop?

2. For good measure, how do you change the BOOT UP artwork and shutdown artwork from the Ubuntu circle, and the color of the progress bar?

3. Last, if that's not too much...is there a keyboard shortcut, while booting and shutting down, where you can see the flow of messages INSTEAD of the progress bar (Windows, for example, you can sometimes press ESC to dismiss the splash screen and see the gory details).  Reason being I see widely varying times in booting and shutting down, and have no idea what phase of the process may be slowing things down.

I'd also like to get a sense of what's going on behind the curtain as a learning experience!

---

### Post by s6dalane on 2006-12-31
I think I can help you with the problem nr 1. It's called a splash screen and you can find many of those [here]("http://www.gnome-look.org/index.php?xcontentmode=160").

---

### Post by teet on 2007-01-01
For number 3, open up a terminal and type:

```
 gksudo gedit /boot/grub/menu.lst 
```

Find the section that looks like this (it's kind of hidden in the middle):

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```

delete the word 'quiet'

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

```

Save and exit.  Reboot.

You should now see some ugly blue text below the progress bar :)

-teet

---

### Post by autocrosser on 2007-01-01
In Order--

1. In Synaptic--search for splash screen--you can add a "Control Panel"  to change to different ones--download more from gnomelook.org

2. There are two ways currently (without going to the terminal;))--currently supported is SUM (works well--I just like the second choice) & Usplash-Switcher. SUM can be found in searching the forums--Usplash-Switcher you can still find in the closed Edgy Development forum---your choice as to which you use (SUM is easier to get--Usplash-Switcher is a program by the guy that coded Usplash--you can see why I like it;))

3. The simplest answer of all--you just need to get your hands dirty (SUM will do this, but it's easy to know how). Open a terminal & type in:

sudo gedit /boot/grub/menu.lst

hit <return> and it will ask for your password <return>

Text Editor will open with "Super user" permissions

Scroll down until you see your first kernel line--mine looks like this:
title        Edgy, kernel 2.6.17-10-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=UUID=1b31b23b-4db9-42c1-84a8-fd1f21992500 ht=on ro splash
initrd        /boot/initrd.img-2.6.17-10-generic
savedefault
boot

the kernel line you have will say "quiet splash"--just remove the "quiet"--save the file & you are done.

You can also add a grub splash image--this will require more editing very close to the same area--for that info---just ask or you can take the easy way out & use SUM:D

---

### Post by puneit on 2007-01-01
For Number 1, I can't give you how to customize it, and if can be done would like to know how.
But for the time being, I have just disabled it. You can do the same by pointing to System--> Preferences--> Sessions
Under Sessions options, un-check "Show Splash screen on login"
This will disable the brown colored nautilius splash.

---

### Post by cmost on 2007-01-01
Let me save you a lot of hassle with two little words:  Linux Mint

It's Ubuntu but with a lot of really nice customizations, a few unique tools and a much more pleasing color scheme.  Fully compatible with the latest Ubuntu.

Check it out here:  [http://lt.k1011.nutime.de/](http://lt.k1011.nutime.de/)

Enjoy!

---

### Post by aysiu on 2007-01-01
#1. The splash screen is in /usr/share/pixmaps/splash
You can press Alt-F2 and type ```
gksudo nautilus
``` to be able to modify that folder

#2. You can modify the splash by using this guide:
[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)

#3. Edit the /boot/grub/menu.lst file using *gksudo nautilus*
Find the kernel line in the entry you boot from (you may have to scroll down a bit). Remove the word *splash* from that line.

---

### Post by allwin on 2007-01-01
Thanks, all.  I used SUM and found a different color splash screen, and turned off the SPLASH keyword in the grub file.  Now down to an acceptable minimum of brown.  Auspicious start to 2007!;)

---

