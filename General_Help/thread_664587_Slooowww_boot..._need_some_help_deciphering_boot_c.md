---
title: "Slooowww boot... need some help deciphering boot chart"
date: 2008-01-11
forum: General Help
---

### Post by tiger.woods on 2008-01-11
I installed boot chart to try and help with my slow boot on my Dell Inspirion 8500 laptop but I don't really know what I'm looking at.

Anyone know how to decipher what is taking so long in the boot process?

Thanks,

---

### Post by chrisccoulson on 2008-01-11
Can you post your bootchart?

---

### Post by tiger.woods on 2008-01-11
yeah sorry about that.... duh!

---

### Post by mcduck on 2008-01-11
For some reason usplash isn't working correctly, and it's using a lot of CPU time during the boot making everything slow. You could either try reinstalling usplash to see if it fixes the problem, or disbale the usplash to use the normal text-based boot instead.

Here's how to disable usplash:

1. run 'gksudo gedit /boot/grub/menu.lst

2. Find the following section and remove the 'splash' (these are the default options that are used during kernel updates to recreate the menu.lst file):
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792 quiet
```

3. Then find the actual kernel boot line, and remove 'splash' from it as well. This is the line that will actually remove the boot splash:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=694c24ca-a0f0-48a4-a34a-6b3a50166e05 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

4. Save the file, reboot, and enjoy the geeky code running on the black background during the boot. Even if you may not find it as pleasing to eye as the graphical boot splash, at least the boot should be a lot quicker now.

---

### Post by tiger.woods on 2008-01-11
Thanks for the post McDuck...

What would the process be for re-installing usplash?

TW,

---

### Post by mcduck on 2008-01-11
```
sudo apt-get --reinstall install usplash
```

(or just find the package with Synaptic Package Manager, right-click, select 'Mark For  Reinstallation' and click 'Apply')

---

### Post by chrisccoulson on 2008-01-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Your problem is indeed with usplash. This is a common bug, and I'm not sure reinstalling usplash will fix it, as this is caused by the installer writing a bad usplash.conf. The workaround is to edit your /etc/usplash.conf, and set the xres and yres to a resolution supported by your monitor, then run:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by tiger.woods on 2008-01-11
I'll give that a whirl, thanks.

Interestingly enough when I booted this machine directly from the CD it was a quick boot. I only got this problem after installing to the hard drive.

TW,

---

### Post by chrisccoulson on 2008-01-11
That is expected, as the problem lies with the /etc/usplash.conf that Ubiquity writes to your hard drive during the install. It will probably contain a resolution to big for your monitor in at least one direction.

---

### Post by tiger.woods on 2008-01-11
Worked like a charm!

Much appreciated guy's thanks.... :)

---

