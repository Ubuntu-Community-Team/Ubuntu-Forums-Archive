---
title: "grub2: hide vista recovery"
date: 2013-02-23
forum: General Help
---

### Post by El Tito on 2013-02-23
Hi everybody.

I followed your instructions step by step, but it seems that grub doesn't identify correctly the $LONGNAME. I copied exactly Windows Recovery Environment (loader):

```
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found initrd image: /boot/initrd.img-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
```

A couple of days ago, I selected accidentally that entry in the grub menu (I was half asleep), and my system was wiped out.

Thanks in advance.

---

### Post by oldfred on 2013-02-23
Moved to a new thread. Old thread may not work with the various new versions of grub as the scripts have changed.

Old thread for reference.
[http://ubuntuforums.org/showthread.php?t=1330700](http://ubuntuforums.org/showthread.php?t=1330700)

You can use grub customizer.
       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

    I still prefer to turn os-prober off and copy only the entries I want into 40_custom rather than edit scripts. Each version of grub has difference and may overwrite script changes. 

       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

    Copy the windows entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy to and edit :
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Ifi you change Windows or add other systems you can turn os-prober back on.

---

### Post by El Tito on 2013-02-24
Thank you so much. 
After removing the executable bit of the 30_os-prober, and adding the desired windows entries to 40_custom, I get rid of the undesired entries.

---

