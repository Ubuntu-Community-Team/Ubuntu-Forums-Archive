---
title: "Question about dual booting"
date: 2014-05-11
forum: General Help
---

### Post by jmeeter on 2014-05-11
I decided before I commit 100% to a distro that I would dual boot Ubuntu and Xubuntu and see after some time which "feels" better to me. Well, after restarting the computer for the first time I saw this screen:

[[IMG]http://i.imgur.com/3bG53dgl.jpg[/IMG]](http://imgur.com/3bG53dg)

I was confused as I saw -two- options for Ubuntu. I know that Xubuntu is a derivative of Ubuntu but why is it showing up as Ubuntu (and not Xubuntu) in GRUB?

---

### Post by Luke M on 2014-05-11
It's normal. All the ubuntu variants call themselves plain "ubuntu".

---

### Post by jmeeter on 2014-05-11
I see. So if one had Ubuntu, Xubuntu, and Lubuntu installed, how would they differentiate them?

---

### Post by LastDino on 2014-05-11
That is normal screen. I'm using Xubuntu and certain Arch fork to dual boot too and my Xubu shows up as Ubuntu in grub.

---

### Post by sammiev on 2014-05-11
Check out this [Thread]("http://ubuntuforums.org/showthread.php?t=1664134") on Grub Customizer, you can even edit the titles to what you want the entry to read.

---

### Post by 3rdalbum on 2014-05-12
> **jmeeter said:**
> I see. So if one had Ubuntu, Xubuntu, and Lubuntu installed, how would they differentiate them?

By the drive (/dev/sda1) but it is highly unusual to dual boot two *buntus. The only difference between Ubuntu and Xubuntu/Lubuntu/Kubuntu is the desktop environment and some end-user software. You can simply install the Xubuntu, Kubuntu or Lubuntu desktop environments and software into Ubuntu and choose between them at the login screen. It doesn't need a dual-boot.

---

### Post by oldfred on 2014-05-12
I have many installs, most for testing something, or just old ones that I should houseclean.
But I find it easier just to turn off os-prober and manually add entries to 40_custom. Then I can edit entry at will.

       Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 


 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

