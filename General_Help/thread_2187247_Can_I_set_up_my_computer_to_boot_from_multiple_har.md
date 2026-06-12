---
title: "Can I set up my computer to boot from multiple hard drives?"
date: 2013-11-11
forum: General Help
---

### Post by jhilp on 2013-11-11
I know this is not a Ubuntu-specific question, but I'm wondering if someone can give me a quick answer anyway.  I'd like to set up my computer with 3 different hard drives; one being my main SSD with Ubuntu, one for Windows, and an extra HHD for trying out other Ubuntu flavors.  I've got the SATA power and data cables to hook up to the motherboard.  My main question is, do I need to do anything special in the BIOS, or can I just hook them all up and choose which one I want to boot from in the boot menu at startup?  Thanks!

---

### Post by philinux on 2013-11-11
> **jhilp said:**
> I know this is not a Ubuntu-specific question, but I'm wondering if someone can give me a quick answer anyway.  I'd like to set up my computer with 3 different hard drives; one being my main SSD with Ubuntu, one for Windows, and an extra HHD for trying out other Ubuntu flavors.  I've got the SATA power and data cables to hook up to the motherboard.  My main question is, do I need to do anything special in the BIOS, or can I just hook them all up and choose which one I want to boot from in the boot menu at startup?  Thanks!

Yep grub is a multi boot loader. Nothing in bios really. It should recognise all the drives. Mine does when i plug in an external.

---

### Post by Dennis N on 2013-11-11
Yes, but there is no boot menu that will come up automatically that I know of - you would have to press the necessary key to see the 'one time' boot menu to boot from a drive other than the one selected to be booted in the bios.

---

### Post by jhilp on 2013-11-11
That's what I meant when I said boot menu: hitting F10 or whatever key that gets you into the one-time boot menu.  Thanks for the help!

---

### Post by oldfred on 2013-11-11
Do not skip a port and start at 0.

I have 4 drives and skipped a port somewhere. Everything works as now UUIDs are used. But when I plug in a flash drive (all mine are bootable) it becomes sde. But since I skipped a port when I reboot flash drive becomes sdb and all the others move up one. Then I have to be careful what drive I am working on.

I got to the point to so many installs, many now obsolete, that I turn off os-prober and just add my own entries to 40_custom for those I want to boot. And I often install different grub verson to different drives. My sda used to be my XP (still is but not used), so all my new installs I now just let it default to sda, so I know booting from sda will be my most recent install usually somewhere on sdc, but sdd is my default boot in BIOS.

---

### Post by Dennis N on 2013-11-11
Just be aware that the OS on each drive (I assume you want only one OS per drive) has its boot loader installed to the MBR of the same drive as the OS is installed on. Then you are ok.

---

### Post by Dennis N on 2013-11-11
There is a side effect that should be mentioned: sooner or later the Ubuntu on Drive A ( and the other drive with Ubuntu) will 'pick up' the OSes on the other drives, and include them in a Grub menu.  You can prevent this by disabling OS prober in the Ubuntu installs if you want.

---

### Post by jhilp on 2013-11-11
How do I disable the OS prober?  And what do you mean by installing the boot loader to the MBR?  Thanks again for the help!

---

### Post by oldfred on 2013-11-11
You can turn off os-prober.
 In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

But you probably want to add your own custom entries.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Attached shows the manual install after pressing the change button. I already had partition with old install of Saucy, so I did not change size but format it and choose it as / (root). Combo box at bottom still shows sda, generally you want to change that to the same drive as you are installing or in my case change to sdc.

---

### Post by jhilp on 2013-11-11
Just to make sure I understand correctly, when you say the Ubuntu drives will pick up the OS's on other drives, you're not saying it will actually transfer files, right?  It just shows up on a Grub menu?

---

### Post by Dennis N on 2013-11-11
> **jhilp said:**
> Just to make sure I understand correctly, when you say the Ubuntu drives will pick up the OS's on other drives, you're not saying it will actually transfer files, right?  It just shows up on a Grub menu?

Right. The other operating systems would just show up on the Grub menu, and you would have a choice to start them up, or start the one on the disk you booted into. If you want to boot directly to the OS on the disk without the grub menu showing, you have to disable the OS prober, which could be done later after you install. This will stop the menu appearing.

---

### Post by jhilp on 2013-11-11
Ok, in that case I won't worry about it.  Thanks!

---

