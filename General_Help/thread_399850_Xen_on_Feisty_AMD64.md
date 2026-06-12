---
title: "Xen on Feisty AMD64"
date: 2007-04-02
forum: General Help
---

### Post by shanepardue on 2007-04-02
I have heard good thing about xen, but I've also heard it's not the easiest to setup and I've 
experienced a little of that. 

I installed the ubuntu-xen-desktop-amd64 package and reboot. While it's booting, it kernel panics 
and fails to mount the filesystem. The only way to even log into ubuntu is to use a generic kernel.

Has anyone experience something similar to this or am I missing something?

---

### Post by shanepardue on 2007-04-22
I've experienced a few problems with a 64-bit setup..I reverted back to the 32-bit and haven't experienced any problems.

---

### Post by bjchip on 2007-04-23
The ubuntu Xen install puts on the vmlinuz-2.6.19-4-generic-amd4 kernel.  You can't get restricted drivers (no nvidia) and the system will come up in 800x600 graphics once we've resolved the disk issue you seem to have.  One of the things I've noticed is that even RAID1 is bad on /boot  for these installs, and lvm... well, I didn't install it for the base installation. 

The xen-ubuntu package has a minor dependency flaw, you apparently need to install bridge-utils before you install xen-ubuntu and create any guests.  

It is also possible that you will need to set up the bridge by hand.  I did this but I also did NOT do the bridge-utils first so I do not know if this will actually work properly if it is done in order.

Overall I found this pretty easy with feisty... compared to some of the past 10 days of 
nightmarish attempts with every other version for which I have an iso :-)

Now have 2 6.06.1 LTS guests running and waiting for me to paint something on them. 

I haven't seen the kernel panic you describe except in terms of the /boot format.  

More info please?  

Thanks
BJ

---

### Post by littlewing27 on 2007-04-29
This sounds similar to the problem i'm having on my intel machine
(apologies ahead of time, i'm a linux newbie)

Here are my steps taken
[LIST]
[*]installed Ubuntu 7.04 with the standard partioning scheme.
[*]downloaded and installed Xen 3.0.2 for 32 bit smp and dependencies (bridge-utils, iproute, etc).  ./install.sh didnt complain and completed successfully.
[*] added this section to /boot/grub/menu.lst , using update-grub command
[INDENT]
title		Xen 3.0.2-2 / Ubuntu, kernel 2.6.16-xen
kernel		/boot/xen-3.0.2-2.gz
module		/boot/vmlinuz-2.6.16-xen root=UUID=fb530b8c-d396-471e-8707-49ad7608dc24 ro console=tty0[/INDENT]

[*] update-rc.d xend defaults 20 21
[*] update-rc.d xendomains defaults 21 20
[*] mv /lib/tls /lib/tls.disabled
[*] **reboot**
[/LIST]

Now when it reboots, kernel panic
[INDENT]
VFS: Cannot open root device "UUID=fb530b8c-d396-471e-8707-49ad7608dc24 " or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[/INDENT]
I've tried changing the 'UUID=..' to /dev/sda1 with no luck

Any help appreciated.

---

### Post by bioborg on 2007-05-07
dunno if this helps, but when I installed feisty on my amd64 on a sata drive at sda1, I had to go back and boot off the live cd and go in and do grub-install '(hd1)' , because my motherboard wanted to boot off of hda, which would normally be hd0, but feisty thought sda was hd0, so hda became hd1.  Just saying, feisty gets confused with device names sometimes.  Maybe this is your issue.  Maybe you can refer to the disk as '(hd0)'
So, I'll get back to you after I try installing xen here... Although, seems to me I might as well just use the xenexpress livecd, with debian etch on it...

---

### Post by explainer on 2007-05-30
So, I'll get back to you after I try installing xen here... Although, seems to me I might as well just use the xenexpress livecd, with debian etch on it...

I have Feisty on a dual core amd64 system with a sata drive.  I downloaded the XenExpress Install CD from the Xen site (is this what you mean by the xenexpress livecd?).  I would like to install the Xen VMM on this system, while retaining the Feisty install I already have, so I select "Convert an existing OS to a Xen VM (P2V)".  The install proceeds until I am asked about DHCP, when I select "Configure all interfaces using DHCP", when I get a reboot and my original Feisty image boots up.  It doesn't look like the Xen VMM installed at all, and I am a bit perplexed.  Has anyone had any experience with this?

---

