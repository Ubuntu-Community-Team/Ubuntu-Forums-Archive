---
title: "Help!  MBR and Grub issue....."
date: 2008-05-07
forum: General Help
---

### Post by ElEdwards on 2008-05-07
I'm in a mess! :(

I've been trying various Linux flavors for the last year, always dual-booting with WinXP.  I inevitably come home to Ubuntu :)

Yesterday, I installed the latest openSolaris but after rebooting, my system kept locking up.... so I decided to give up on that and reinstall Ubuntu 8.04...
BUT near the end of the installation process, Grub had a "fatal error" and the install quit!!

I can only guess that openSolaris does something to the MBR that is different from all the Ubuntu's I've used....but right now, my laptop is a very nice paperweight.  I can't boot into anything!  All I get is 4 characters of gibberish in a small red rectangle.

If I boot to the 8.04 LiveCD, I can see my Windows partition and the **/** and **/home** partitions from the Ubuntu install but I can't boot to either one, since there is no Grub menu on boot up.

Any thoughts?  I'd like to burn a SuperGrub CD....but my laptop contains the only burner I own.

Help!  Please help!

Thanks :)
El

---

### Post by michaelaly on 2008-05-07
You can use this HowTo : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29)
to reinstall GRUB using the LiveCD, should fix you right up.

---

### Post by ASULutzy on 2008-05-07
I may be way off base with this, but if you can boot into the live-cd, why can't you simply reinstall grub? Mount the half-broken install from the live cd and edit its /boot/grub/menu.lst appropriately

just do sudo grub from a terminal and then (these will need to be adjusted per your system)
>root(0,2)
>setup(hd0)

Where hd0 is the MBR for the HDD where grub needs to install to load on boot
and where hd(0,2) is the partition that contains your grub files.

Oh, there's a nice little tutorial I found
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

edit: awe, bummer, got beat to it ;)

---

### Post by ElEdwards on 2008-05-07
When I booted back up to the LiveCD, I looked in the **/** that was created by the installation.  There was NO Grub directory in Root, no doubt due to the fatal error during the installation. :(

El

---

### Post by chokfulla on 2008-05-07
> **ElEdwards said:**
> When I booted back up to the LiveCD, I looked in the **/** that was created by the installation.  There was NO Grub directory in Root, no doubt due to the fatal error during the installation. :(

El

  There won't be a grub directory in root.  The grub directory is here --> /boot/grub/
  Hope that helps.

---

### Post by zvacet on 2008-05-08
Just follow instructions from link **michaelaly** posted to you.

---

### Post by ElEdwards on 2008-05-08
I misspoke/mistyped..... there was no Grub in /Boot.

I fixed everything last night:
1) used SuperGrub to restore my MBR
2) used GParted to delete and recreate my Linux partitions
3) installed DreamLinux 3.2
4) happer camper :)

I've tried Ubuntu 8.04 three times on my laptop (Compaq Presario 2170us) but Hardy just doesn't like my older video and audio.  I get TONS of vertical lines in my LCD and crackles in my audio.

Thanks :)
El

---

### Post by nnamdi on 2008-05-08
hello man u could try out this link it should help you 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by nnamdi on 2008-05-08
hello man u could try out this link it should help you 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

