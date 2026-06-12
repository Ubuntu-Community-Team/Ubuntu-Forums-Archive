---
title: "grub doesnt start kubuntu goes to initramfs"
date: 2007-11-27
forum: General Help
---

### Post by fatmano on 2007-11-27
Ok so I just got an hp dv9000, I tried installing w/ live cd, no luck....I tried installing w/ alternate cd and had some luck. The live cd stalled when installing the generic-linux-kernal then would spit me out in to a red screen with an error (cant really remember what it was, but the CD was checked twice and record speed dropped to 4x ). I was able to get past that with the alternate cd, but it still would not completely install. What I ended up doing was each step on its own in rescue mode. That at least got me to here. I got my nVidia drivers running w/ envy ( I highly recommend it for anybody who is having problems w/ their nVida card ). But I was hardwired at the time. I got the wireless running using the ndiswrapper and getting the driver from a previous post on hp. My biggest problem now is that grub does not seem to recognize my sata drive. It works fine if edit the kernel line, any tell it exactly where it is ie not using the UUID, If I edit the root= to be root=/dev/sda1 it will boot. If I edit the /boot/grub/menu.lst to always read root=/dev/sda1 it will light my hard drive light and then drops to a :
initramfs> 
prompt. This is where I see that my /dev/sda1 is not mounted to boot from.  All I really need to do is edit my kernel line and then press b and it works great. Now can I say what a PITA that really is....

I am sure I am missing something really simple, I just cant find anywhere. Please help,
I am committed to making Gutsy work, and other than having to issue my essid for my bcm4312 ( which I dont like having to either, but can sort of live with ) I have made this Gutsy my OS of choice and want to stick it out.

I upgraded from Fiesty on my work desktop in ~40 mins. It went great, that is what started me down this road. I can go backwards if need be, I already dropped from the AMD-64 to x86-32 to get to where I am now. But if I could get that grub thing fixed I am going to stay.


-eo
HP dv9000
2GB
SATA 160GB
AMD-64
Broadcom 4312 a/b/g ( rev 2 )


====Follow-up===
dopey:/boot/grub$ /usr/lib/klibc/bin/kinit
  argc == 5
  argv[0]: "/usr/lib/klibc/bin/kinit"
  argv[1]: "root=/dev/sda1"
  argv[2]: "ro"
  argv[3]: "quiet"
  argv[4]: "splash"
  argc == 3
  argv[0]: "IP-Config"
  argv[1]: "-i"
  argv[2]: "Linux kinit"
IP-Config: no devices to configure
kinit: do_mounts
kinit: name_to_dev_t(/dev/sda1) = sda1(8,1)
kinit: root_dev = sda1(8,1)
kinit: failed to identify filesystem /dev/root, trying all
kinit: trying to mount /dev/root on /root with type cramfs
kinit: Cannot open root device sda1(8,1)
kinit: init not found!

I have not /dev/root where is it getting this from....could this be my issue???

---

### Post by fatmano on 2007-11-28
ok, so I guess I am stuck based on this link....

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/57881](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/57881)

](*,)

---

