---
title: "Installing Vista in kvm fails"
date: 2007-09-17
forum: General Help
---

### Post by fogster on 2007-09-17
I'm running Feisty an Intel Core2Duo laptop, supporting hardware virtualization. I have a 32-bit Vista install DVD. I installed kvm, created a 10GB image, and tried to boot the installer.

When I do...

```
# kvm -no-acpi -m 768 -cdrom /dev/cdrom -boot d windows.img
```

Vista's installer fails with an error that ACPI is unsupported.

For a minute I thought it was super-simple, and just removed the --no-acpi option from the above command. But then the installer comes up with a blue stop error screen and dumps a core.

I also experimented with the memory size... I have 2GB physical RAM, but tried dropping 768 down to 512. It doesn't make a difference.

Can anyone help me figure out how to get around this?

---

### Post by aztechclan on 2007-11-09
I am installing Vista in Gusty with KVM.  Make sure you have the kvm-intel (or amd) module installed.  Also, make sure that the CD drive is accessible.

I'm using this command to boot it:

kvm -m 1000 -cdrom /dev/cdrom -boot d visual-studio.img

So far I'm half way through the installation and all is well.  If it fails miserably I will come back and update this post.

---

### Post by aaahoopy on 2007-11-13
I got vista to install quite nicely with the following command:
sudo kvm -m 1024 -localtime -net nic,model=rtl8139 -net user,vlan=1 -cdrom /opt/iso/vista/vista_en_dvd.iso -boot d basevista.img

EDIT: vista will not install without ACPI - but where it crashed vigorously in XP it worked fine in vista.

The standard NIC that would get used if -net was not specified is too old for vista and does not have drivers.  

Next up, I found if I take away the cdrom image that kvm always crashes with an exception 13 instantly after startup.  Fine, I just leave it in, and if I need to access a different CD, I use ctrl-alt-2 to change the cdrom ISO manually after booting.

EDIT: The cdrom I am using is an MSDN cdrom and has some sort of boot menu selection thingy.  This may be important for the exception 13 issue.

The only problem I have left is the network does not work.  I have compared with a windows XP instance running side by side, and I cannot make the standard network settings work at all.  I even tried replicating the settings windows XP gets automatically with no luck.  I am going to try the TUN settings and see if that gets me anywhere.  

I need to access vista soon to be able to write some documentation for some users I am supporting.  If anyone can unravel the network issue, I would love to hear about it.

---

### Post by aaahoopy on 2007-12-20
> **aaahoopy said:**
> 
EDIT: The cdrom I am using is an MSDN cdrom and has some sort of boot menu selection thingy.  This may be important for the exception 13 issue.


Slap my butt and call me crazy, but this matters.  I managed to get ubuntu server to install into kvm by running *kvm -no-kvm* (because the core2duo sucks) and going through the install.  Then I could not get it to boot without the -no-kvm, despite the fact that there is no splash screen.  

Long story short, I set the CDROM to one of the MSDN cdroms that has an optional boot (shows this message on boot: press space bar to boot off of CDROM), and now it works.  YAY.

Good luck.

---

