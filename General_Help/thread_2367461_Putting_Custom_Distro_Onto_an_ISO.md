---
title: "Putting Custom Distro Onto an ISO"
date: 2017-07-30
forum: General Help
---

### Post by emilward on 2017-07-30
So basically I have a Ubuntu respin that I'm trying to put onto an ISO to pass out to some friends/family. I've tried UCK and Respin but they don't work. I am wondering if it is because I used the Ubuntu Mini ISO instead of traditional Distro. It's extremely minimal using lightdm, openbox, xfce4-panel, nitrogen, lxtask, gnome-terminal, some wallpapers, firefox, a startup script, and that's it. Gives you a very minimal Ubuntu base and users have full control over what gets installed, no-bloat but still functional. Any idea how I can get this onto an ISO? UCK asks to use the ISO I'm using and when I point it too the mini ISO and install it in VirtualBox, it doesn't install properly. Respin will install and load the login manager but the desktop doesn't load. Any ideas what I am doing wrong?

---

### Post by &amp;KyT$0P# on 2017-07-30
Does it work if you use [this method]("https://help.ubuntu.com/community/LiveCDCustomization")?

If you need to be able to EFI-boot the system, when you're ready to actually create the new ISO follow [these steps]("https://linuxconfig.org/legacy-bios-uefi-and-secureboot-ready-ubuntu-live-image-customization#h5-creating-a-boot-able-isohybrid-iso-image") instead of the [FONT=Courier New]mkisofs[/FONT] command.

---

### Post by sudodus on 2017-07-30
If you make the network portable, which you can do according to this link,

[Unmanaged Wired Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

and avoid proprietary drivers, your Ubuntu respin might be portable enough as it is, an installed system.

You can try, for example by making a cloned image for example with [Clonezilla](http://clonezilla.org), and then install from that image to another computer (with a drive of at least the same size).

If this works, it is much easier than to create an iso file.

An alternative if it is enough for the system to work in BIOS mode (not UEFI mode) is to create a tarball with and for the [One Button Installer](https://help.ubuntu.com/community/OBI).

---

### Post by emilward on 2017-07-30
Awesome, thanks for the replies and suggestions. I'm already seeing some steps I missed. I will definitely try these out later tonight or tomorrow. Hopefully you guys won't hear back from me! Thanks again!

---

