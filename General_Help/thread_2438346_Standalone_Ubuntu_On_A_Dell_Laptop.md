---
title: "Standalone Ubuntu On A Dell Laptop"
date: 2020-03-10
forum: General Help
---

### Post by box02-0 on 2020-03-10
[SIZE=2]Hi.

I&#8217;ve installed a second drive (SATA SSD) [/SIZE][SIZE=2]on a [/SIZE][SIZE=2]Dell [/SIZE][SIZE=2]Windows 10 [/SIZE][SIZE=2]Laptop, [/SIZE][SIZE=2]and [/SIZE][SIZE=2]installed Ubuntu 18.04 (ISO) onto it.[/SIZE]

 [SIZE=2]Prior to the installation, I made an Ubuntu partition on the SATA SSD on my Desktop, and copied (Gparted) my Desktop live Ubuntu onto it.[/SIZE]

 [SIZE=2]Ubuntu boots just fine on the Dell, however the system is not quite the same as the Ubuntu on my Desktop. Application menus are not quite right either. I use UNITY on my Desktop, and the Dell Ubuntu appears to be using GNOME. The ala-carte icon and other icons are not appearing on the top menu bar, Cairo dock is not there, side bar launcher icons are missing,&#8230; Close but not quite right. I can fix it all but that&#8217;s tedious.[/SIZE]

 [SIZE=2]Now my Question &#8211; how to make the Dell Ubuntu identical to my Desktop Ubuntu?[/SIZE]

 [SIZE=2]My first instinct was to re-copy my Desktop Ubuntu onto the Dell Ubuntu. UUID&#8217;s are identical, but I would think that GRUB and FSTAB are not. Should I make a copy of the Dell GRUB & FSTAB, and then restore them after the Desktop to Dell Ubuntu copy? Are there other files besides GRUB & FSTAB to consider?[/SIZE]
 
 [SIZE=2]Any thoughts would be greatly appreciated.[/SIZE]
 
 [SIZE=2]Thanks,[/SIZE]
 [SIZE=2]M...[/SIZE]

---

### Post by dragonfly41 on 2020-03-10
This sounds like you are in a gnome-flashback session rather than Unity.

[https://www.omgubuntu.co.uk/2019/06/enable-gnome-classic-mode-ubuntu](https://www.omgubuntu.co.uk/2019/06/enable-gnome-classic-mode-ubuntu)

At login you should be able to change modes by clicking on button.

---

### Post by crip720 on 2020-03-10
Ubuntu 18.04 ISOs and onwards uses gnome desktop as default(installed).  You need to install unity desktop if you want unity.  It works well with no inference with gnome.  You don't mention witch ubuntu you installed on your desktop, so imagine it was an earlier version.

---

### Post by box02-0 on 2020-03-11
Ubuntu 18.04 copied from my Desktop is from June 2018. It is up to date on all software patches.  The ISO install on the Dell is from a recent 18.04 download.

Should I copy everything in my Desktop Home directory to the Dell Home directory?

Thanks for the responses.
M...

---

