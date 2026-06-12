---
title: "Slow boot?!?!?"
date: 2007-05-17
forum: General Help
---

### Post by hammedhaaret on 2007-05-17
Hi again.

I've got Feisty on a laptop with a Core 2 dual 1.80 Ghz CPU, 1 gb DDR RAM a geforce go 7600 gt 512mb and a 80gb 5400rpm hdd

even though it takes more than a while to boot and I've even managed to make a cup of tea, boiling water and everything, before it was done... said in another way: it takes several minutes.

the loadbar stops at about a third of the way and stays there for some time before it finishes up and shows the login screen.

anyway to tweak it to boot, hopefully a lot, faster?

And if i need to add a -nosplash option in some grub boot menu thing... could you please specify how i should do.  I am pretty new to linux

yours sincerly.... :P hammedhaaret

---

### Post by Quintin Riis on 2007-05-17
There is a server timing out trying to resolve names.  What sort of network servers are installed on the machine?

---

### Post by hammedhaaret on 2007-05-17
dunno really? i got wireless network which is the only i use... no servers

---

### Post by PacShady on 2007-05-19
I've got the same problem on my laptop, running Kubuntu Feisty.

The progress bar would stop at about a third of the way for quite some time, before continuing boot. I disabled usplash to see what it was, and it's stopping at configuring network interfaces. I suspect it has to do with wireless. Is there any way of stopping it configuring the wireless until after I boot, since I usually need to log in and such when I use it with KNetworkManager anyways, so it's not gonna find much to begin with.

'Shady

---

### Post by PacShady on 2007-05-19
I found a fix that seems to work well on Kubuntu, don't know about vanilla Ubuntu though.

Simply edit /etc/network/interfaces using your favourite editor, and comment out all interfaces except for the loopback one. Since KNetworkManager handles network interfaces, it picks it up after boot. Voila, shaved off about 30 seconds off my boot time!

'Shady

---

### Post by Ub1476 on 2007-05-19
Hi, saw this thread, and your fix worked perfect for me too!

Thanks:)

---

### Post by JTC2006 on 2007-05-19
hi,
anyone know if this works on standard ubuntu, and if so, how do I comment the lines out?

---

### Post by SnowLinux on 2007-05-19
I also have a slow boot issue.

When the boot progress bar appears it takes over 2 minutes for it to start to move across
to the right. I've tried the editing of the interfaces file, commenting out as suggested
but no improvement!

I did manage to sort an RSDP issue I had by adding 
pci=noacpi acpi=off    to menu.lst file as suggested in another thread.

My system is Edubuntu 7.04 with 
750mhz Barton CPU, 
512mb SDRam,
onboard LAN & 32MB graphics.

Once booted the system is quite good speed wise for the spec, just need to sort the slow boot out!

---

### Post by SnowLinux on 2007-05-19
Adding to what I've reported above,
I just used the CTRL+ALT+F1 technique on booting and the screen is displaying stuff like

ata1.00: exception  ........ a load of zeros and numbers then comments that its frozen

then the very next line is

ata1.00: cmd


anyone got an idea on this please?

---

### Post by Quintin Riis on 2007-05-19
> **PacShady said:**
> Is there any way of stopping it configuring the wireless until after I bootDelete or comment out any lines in /etc/network/interfaces that refer to your wireless interface.

---

