---
title: "Acessing Windows (Dual Boot) Partition within VMWare"
date: 2007-08-23
forum: General Help
---

### Post by rla128 on 2007-08-23
I'm dual-booting Ubuntu 7.04 and Vista.

In Ubuntu, I have a virtual XP installation using vmware server.  

Is there a way to get at my Vista partition (currently mounted to media/sda1) from within the vmware xp installation?  I want to be able to play my music from my Windows partition.

Many thanks.

-Robert

---

### Post by DalekClock on 2007-08-23
*ORIGINAL MESSAGE WAS INAPPROPRIATE TO YOUR PROBLEM*

Sorry, my mistake. I didn't read it properly first time round, so you can forget what I originally typed.

---

### Post by AbredPeytr on 2007-09-01
Hi,

wouldn't it be easier to play your music that is located on your Vista partition in Ubuntu? For that you just need to install ntfs-3g from Synaptic Package Manager, then you can read and write to your Vista partition from Ubuntu and only have to use the Virtual Windows XP for whatever Windows program you need.

Hope this helped and didn't annoy.

---

### Post by rla128 on 2007-09-17
It's through Urge, and therefore has drm.

I'm beginning to get annoyed with drm, even though the subscription model is nice.

It'd be sweet if I could somehow Virtually load my Vista installation while in Ubuntu, though.

---

### Post by nxt on 2007-11-28
just looking at the same problem....I found this:

Run Existing Windows Installation on Ubuntu with Vmware Player
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

however this creates a copy of the original partition to be used with vmware player  :(

---

### Post by eriqjaffe on 2007-11-28
> **nxt said:**
> just looking at the same problem....I found this:

Run Existing Windows Installation on Ubuntu with Vmware Player
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

however this creates a copy of the original partition to be used with vmware player  :(That doesn't create a copy of the partition, I've used that very same procedure before and it works perfectly.  You **do** have to create a second "Hardware Profile" in XP to get around the IDE driver differences, but you're directly accessing the partition rather than creating a .VMDK file.

...and it's probably a good idea to increase the GRUB timeout so you don't accidentally try to boot into Ubuntu within Ubuntu...I can't imagine much good coming of that.

---

