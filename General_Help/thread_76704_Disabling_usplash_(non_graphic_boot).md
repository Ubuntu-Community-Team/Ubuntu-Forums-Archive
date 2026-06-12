---
title: "Disabling usplash? (non graphic boot)"
date: 2005-10-15
forum: General Help
---

### Post by egas77 on 2005-10-15
While I love all the modern and up-todate packages in Ubuntu, I'm an old codger in some ways, and still prefer an non graphical start-up for Linux.

Is there a way to go back to Hoary style behaviour? I don't see anything in grub's menu.lst file that would allow me to switch this off, and any attempt at uninstalling usplash results in ubuntu-desktop being removed too.

Thanks much.

---

### Post by SickTwist on 2005-10-15
sudo apt-get remove usplash

---

### Post by egas77 on 2005-10-15
If one tries that, Ubuntu wants to uninstall ubuntu-desktop as well, and I'm guessing all sorts of nastiness will happen if I try that. 

I tried uninstalling usplash from both Synaptic and apt-get, the result is the same, it says I need to remove ubuntu-desktop

---

### Post by Wombley on 2005-10-15
[QUOTE=egas77]If one tries that, Ubuntu wants to uninstall ubuntu-desktop as well, and I'm guessing all sorts of nastiness will happen if I try that. 

I tried uninstalling usplash from both Synaptic and apt-get, the result is the same, it says I need to remove ubuntu-desktop[/QUOTE]

ubuntu-desktop is just a meta package - it depends on all the other desktop packages (obviously including usplash) but doesn't provide any functionality itself. As long as you reinstall it before doing a new distribution upgrade removing it is fine...

---

### Post by aleksabl on 2005-10-15
sudo gedit /boot/grub/menu.lst

And remove the word splash from this section:

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet section
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

---

### Post by jeremy on 2005-10-16
[QUOTE=aleksabl]sudo gedit /boot/grub/menu.lst

And remove the word splash from this section:

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet section
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot[/QUOTE]
You appear to have replaced 'splash' with 'section' in your example, is this correct?

---

### Post by aleksabl on 2005-10-16
lol, haha. Yes, you're right. Sorry about that!

---

### Post by pizzach on 2005-10-16
Thank you so much!  That did it.  :)  It's been a little while, but doesn't the non-graphical boot seem less colorful or something?

---

### Post by factotum218 on 2006-10-21
> **pizzach said:**
> Thank you so much!  That did it.  :)  It's been a little while, but doesn't the non-graphical boot seem less colorful or something?

are you being serious? LOL

---

