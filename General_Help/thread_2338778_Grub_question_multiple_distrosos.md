---
title: "Grub question multiple distros/os"
date: 2016-10-01
forum: General Help
---

### Post by terry_gardener on 2016-10-01
Hello 

i have multiple distros installed at the moment manjaro, linux mint 18, ubuntu 16.04, ubuntu 16.10 and windows 10. using the bios/legacy mode on motherboard,
What i have found is that when one of the distros update the kernel it doesn't always update on grub so you have to use the submenu for the distro and select the kernel you which to use. 
i have also used grub customiser to change the order of the grub menu, don''t quite know if this caused this problem in first place or not but how do i solve this.

---

### Post by Keith_Helms on 2016-10-01
I usually have 3 Linux installs on my laptop - currently Xubuntu 14.04 and 2 copies of Xubuntu 16.04, but sometimes copies of Ubuntu or Mint to play with.  What I've found is that each distro installs grub and changes the master boot record of the hard drive to point to the latest install.  At that point, new kernel updates to the other 2 distros don't get picked up automatically by the latest grub.  You have to boot the distro last installed, then run update-grub to get those kernels added to the list.  Sometimes the software updates of one of the distros will update grub, change the mbr under the covers, and then THAT distro is now "king of the hill" of the grub menu.

It's a little bit of a pain, but once you understand what's going on, it's easy to manage.

---

### Post by oldfred on 2016-10-02
The work around that I use is documented in this link.
You turn off os-prober, and create your own 40_custom to boot the partition.
Ubuntu and I think all Debian Linux create a link to the most current kernel in /. So you boot the link not a specific kernel in entry in 40_custom.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by DuckHook on 2016-10-02
> **Keith_Helms said:**
> …+1

What I do is:

[LIST=1]
[*]Decide which distro I want to be, as Keith_Helms puts it, "king of the hill" 
[*]Every time another distro update usurps control of GRUB, I boot into my 'king of the hill" distro and:```
sudo grub-install
```
[*]This rewrites the MBR to point to your "king of the hill" GRUB. It is critically important to be running this command within your "king of the hill" distro. If you run it from one of your secondary distros, it will turn that one into the new "king of the hill".
[*]Remember to always run:```
sudo update-grub
```…afterwards, to capture your kernel changes in those secondary distros.
[/LIST]

---

### Post by terry_gardener on 2016-10-03
thanks

---

### Post by DuckHook on 2016-10-03
If you consider your question answered:

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

