---
title: "Grub issue fro second Linux installation"
date: 2008-05-31
forum: General Help
---

### Post by qwallis on 2008-05-31
Hello,
I used to run Opensuse10.2, then I installed Ubuntu and could choose which to boot into: but either after an upgrade in Ubuntu or Opensuse (10.2 to 10.3) I can't boot into Opensuse anymore. Grub reports file missing.

Here is my menu.list

[INDENT]title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4838bb89-465b-4c5c-b3dd-107843a6027c ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4838bb89-465b-4c5c-b3dd-107843a6027c ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4838bb89-465b-4c5c-b3dd-107843a6027c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4838bb89-465b-4c5c-b3dd-107843a6027c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4838bb89-465b-4c5c-b3dd-107843a6027c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4838bb89-465b-4c5c-b3dd-107843a6027c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		openSUSE 10.3 - 2.6.22.9-0.4 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22.9-0.4-bigsmp root=/dev/disk/by-id/scsi-SATA_SAMSUNG_HD321KJS0MQJ1KLC15099-part2 vga=0x31a resume=/dev/sda1 splash=silent showopts 
initrd		/boot/initrd-2.6.22.9-0.4-bigsmp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Failsafe -- openSUSE 10.3 - 2.6.22.9-0.4 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22.9-0.4-bigsmp root=/dev/disk/by-id/scsi-SATA_SAMSUNG_HD321KJS0MQJ1KLC15099-part2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd-2.6.22.9-0.4-bigsmp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		testing
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22.5-12-bigsmp root=/dev/disk/by-id/scsi-SATA_SAMSUNG_HD321KJS0MQJ1KLC15099-part2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd-2.6.22.5-12-bigsmp
savedefault
boot[/INDENT]

How do I find out what to change so that I have the option again?
I would still use Ubuntu mainly, as this problem has been with me for some time and I've really grown into Ubuntu. But, the idea of half my hard drive sitting there doing nothing niggles somewhat.

Any help appreciated.
Thanks in advance.

---

### Post by Rasitiln on 2008-05-31
What is hd0,3 and hd0,2 hd0,0? 

My suggestion is edit the open suse boot line changing the hd0,* to 3 2 0 etc so on until you find the one that boots it assuming that ubuntu fudged up detecting how your hardisk was layed out as it did for my install. Then once fixed go into your /boot/grub/menu.1st and edit the opensuse settings as needed. IE fix the hd0, setting.


hope I'm being clear on this if not just ask question yea? :)

---

### Post by qwallis on 2008-05-31
> **Rasitiln said:**
> What is hd0,3 and hd0,2 hd0,0? 

My suggestion is edit the open suse boot line changing the hd0,* to 3 2 0 etc so on until you find the one that boots it assuming that ubuntu fudged up detecting how your hardisk was layed out as it did for my install. Then once fixed go into your /boot/grub/menu.1st and edit the opensuse settings as needed. IE fix the hd0, setting.


hope I'm being clear on this if not just ask question yea? :)

I think I get what you mean, and to test I just keep rebooting I guess...

---

### Post by Rasitiln on 2008-05-31
Good let me know if it works :)

---

### Post by qwallis on 2008-05-31
I've tried (hd0,1) (hd0,2) and (hd0,3) but that didn't work.

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Testing openSUSE 10.3 - 2.6.22.9-0.4 (on /dev/sda2)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22.9-0.4-bigsmp root=/dev/disk/by-id/scsi-SATA_SAMSUNG_HD321KJS0MQJ1KLC15099-part2 vga=0x31a resume=/dev/sda1 splash=silent showopts 
initrd		/boot/initrd-2.6.22.9-0.4-bigsmp
savedefault
boot

Is that what you meant?

---

### Post by ajgreeny on 2008-05-31
Simply mount your open suse partition in ubuntu and see what the menu.lst file in open suse says.  Now copy the grub entries from that to the ubuntu menu.lst file and you should be good to go.

---

### Post by Rasitiln on 2008-05-31
> **ajgreeny said:**
> Simply mount your open suse partition in ubuntu and see what the menu.lst file in open suse says.  Now copy the grub entries from that to the ubuntu menu.lst file and you should be good to go.

Smooth solution I didn't think of that. I'm so use to horrid windows installations. Unless of course opensuse is using lilo :) But lets hope it isn't.

---

### Post by louieb on 2008-05-31
Just wondering can you browse your open suse partition? 
go to the /boot directory.  More that likely when you upgraded open suse the name of the kernel changed.  make sure the kernel... and the inited... file names are the same as what you have in Ubuntu's GRUB.

```
kernel /boot/vmlinuz-2.6.22.9-0.4-bigsmp
initrd        /boot/initrd-2.6.22.9-0.4-bigsmp

```

just saw aj'greenys - yea his is easier.

---

### Post by qwallis on 2008-05-31
@ajgreeny:  That did the trick!

Thank you all for your help.
I must say Opensuse feels a bit wooden now. I'm not sure what window manager it's running (I didn't realize it had been so long, over 250days), but there's no compiz etc...

Now it's just a question of whether I'm brave enough to hit that "update" icon...

---

### Post by meierfra. on 2008-05-31
To avoid the problem you just had I recommend using the [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#Second_method_configfile_boot") method.

---

