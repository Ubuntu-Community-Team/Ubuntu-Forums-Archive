---
title: "Dual OS booting, I want to boot Linux primary!"
date: 2015-04-07
forum: General Help
---

### Post by essxiv on 2015-04-07
Hey guys,

Just wondering, is there anyway to start up my computer and not having to go through my Windows OS (8.1), and getting right into my Linux OS?

it's just a bothersome always having to enter 2 password, and taking the initial 3-5 minutes..

Thanks!

---

### Post by sudodus on 2015-04-07
Yes, the normal way is to install Windows first (or that Windows comes with the computer). Then install your Ubuntu flavour (and / or other linux distros). Then you will boot via a grub menu (which comes with linux), and the linux distro that was installed most recently will be number one in the grub menu.

Please explain how you have installed linux!

---

### Post by oldfred on 2015-04-07
Somewhat depends on brand/model computer. What is yours?
If Windows pre-installed then it is UEFI which is often an issue.

With UEFI, you can do work arounds to set a hard drive boot entry as really being grub and those systems that only boot Windows will still boot a hard drive directly. If that then is grub, you can just boot.
Some systems require a password and you then can "allow" ubuntu entry to be valid without other work arounds.

If you want to read ahead see link in my signature.

---

### Post by essxiv on 2015-04-28
> **oldfred said:**
> Somewhat depends on brand/model computer. What is yours?
If Windows pre-installed then it is UEFI which is often an issue.

With UEFI, you can do work arounds to set a hard drive boot entry as really being grub and those systems that only boot Windows will still boot a hard drive directly. If that then is grub, you can just boot.
Some systems require a password and you then can "allow" ubuntu entry to be valid without other work arounds.

If you want to read ahead see link in my signature.

Windows 8 was pre-installed when I bought this computer.

Does anyone know any youtube tutorials to make Linux my primary boot OS ? 
Hopefully I will not need a USB, because I don't have one right now.

---

### Post by sgage on 2015-04-28
> **essxiv said:**
> Windows 8 was pre-installed when I bought this computer.

Does anyone know any youtube tutorials to make Linux my primary boot OS ? 
Hopefully I will not need a USB, because I don't have one right now.

So you have Linux installed, and can get into it from the Windows 8 boot menu? If so, give grub the MBR. In Linux, do the following:

sudo grub-install /dev/sda
sudo update grub

That will make the grub menu come up at boot time. You can tweak timeouts and defaults by editing /etc/default/grub.

---

### Post by oldfred on 2015-04-28
If Windows is UEFI and you have to reboot to get to Ubuntu, you may have installed Ubuntu in BIOS mode. 
Or it could be just some systems will not let you set ubuntu entry in UEFI as an option and have to do a work around. One of the many work arounds is what you are doing, but that in effect is using the UEFI one time boot. But from Windows then your are rebooting back to UEFI and its one time boot entry.

You are living very dangerously. Which some may like. :)
It took me several days (had to go to store to buy another flash drive), 5 DVDs and two flash  drives to fully backup my new Windows install. But I made a Windows recovery about 8GB, a Dell recovery - 3 DVDs, and full backup of Windows about 25GB and two more DVDs, one Linux boot and one Windows PE boot to restore image.

But which of the other work arounds may be best depends somewhat on brand & model computer. 
A few will let you directly set ubuntu entry in UEFI as first. 
Some will directly boot ubuntu boot entry if you use the UEFI/BIOS/System boot key often f12 or f10 before system starts booting operating system. If UEFI has fast boot you have to turn that off to be able to get into UEFI or boot key.
Others require copying files into /EFI/Boot folder in efi partition. But again you really need to backup efi partition to another drive before making any changes.

---

