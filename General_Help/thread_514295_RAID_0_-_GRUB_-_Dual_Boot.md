---
title: "RAID 0 - GRUB - Dual Boot"
date: 2007-07-31
forum: General Help
---

### Post by Colosus on 2007-07-31
Hey all.

I've got a particular problem with Ubuntu Fiesty, GRUB, RAID and Dual Booting. Here's my setup:

I have a 2x250 RAID 0 array running off nVidia SATA controller and a Single SATA 80gb drive not part of the array. I had XP installed on the RAID array for quite some time. I decided to install Ubuntu on the 80gb drive so that I could dual boot.

I installed Ubuntu. It detected the array as 2 separate drives (because the livecd has no software raid support). I continued the install to the 80gb drive. Everything went fine. I reboot and Grub pops up and loads Ubuntu immediately.

I am assuming grub was installed to the MBR on the array as the array is the primary drive. My question to all of you...

If I get dmraid installed and setup the array in Ubuntu. Can I then modify grub.conf to also list the Windows install? Have I completely screwed the pooch on my windows install or will fixmbr from recovery bring that back so that I can attempt the longer grub install from the livecd? Any help would be appreciated.

---

### Post by Crakie on 2007-07-31
You should try installing from the alternate install CD. It has raid support. I am a bit confused though... you use a raid controller, but you need software raid anyway? I thought the whole point of a raid controller was that the OS 'sees' a single drive without any drivers?

I am not sure how you could reconfigure Grub to show a boot menu, but the fixmbr thing should work just fine to be able to boot into XP again.

---

### Post by Colosus on 2007-07-31
The nVidia RAID controller is not a true raid controller. The OS still has to have drivers (a floppy disk when installing XP) in order to see the array. It's not like an Adaptec RAID controller, it's just the on-board nforce stuff.

---

### Post by Crakie on 2007-08-01
I see. Someone may correct me on this, but you will have a hard time getting Linux to read that XP array: the drivers for it are not around. I would advice you to leave it alone. Just install Ubuntu on the extra drive you have. You might actually consider disconnecting the array, install Ubuntu (and Grub) and then reconnecting it again.

---

### Post by fjgaude on 2007-08-01
From what I know you have to have Windows running in order to read the Win fakeraid array.

But you can use the fakeraid if you set it up for use by Linux, not as a Windows partition or array:

sudo dmraid -ay
sudo dmraid -r
sudo mkfs -t ext3 /dev/mapper/sil_ahahbhbjaddg
sudo dmraid -s
mkdir /raid
sudo mount -t ext3 /dev/mapper/sil_ahahbhbjaddg /raid

I'm not sure what the nvidia controller tag is (man page says it is simply "nvidia"), but Silicon Images is sil.

The sil_ahahbhbjaddg is the array. It was made by your nvidia program in your BIOS. Notice that the mkfs sets up the array as a Linux filesystem. Do a man dmraid to learn more of the fakeraid characteristics.

frank

---

### Post by locque on 2007-08-20
I am running a similar setup... I have an MSI nForce based MOBO and am running both windows and Ubuntu using dmraid... I have never had a problem reading my NTFS partition. When I run: dmraid -ay it adds my NTFS partition as a new device... 

I can mount the NTFS raid just like any other partition:
sudo mount /dev/mapper/nvidia_gdbdbejf2 /mnt/windows


Not a problem!!!

---

### Post by fjgaude on 2007-08-20
dmraid works fine with MB nvidia fakeraid arrays. I did that for sometime without any troubles. To both read and write to Windows' NTFS files be sure to install ntfs-3g by using Synaptic or apt-get. Then you'll be a happy camper. Make a mount point, as stated earlier, then:

```
sudo mount -t ntfs-3g /dev/mapper/nvida_ahahbhbjaddg /raid
```

Of course the "ahahbhb.... " is unique to your array.

frank

---

### Post by zveroboy on 2007-10-09
But how do you make grub see the WinXP raid set, so that the user can choose at boot time which operating system to boot into?

Many thanks in advance.

---

### Post by DraK on 2007-10-12
Ok, if I am reading this right there is hope that I can access my Sil3114 Raid set which ahs a NTFS partition on it through Linux?

If so great!!

Trouble I am having is that Linux says it does not have an NTFS partition...

Any ideas?

dmraid see's the raid, it is active and both drives are listed to.

---

### Post by fjgaude on 2007-10-12
> **zveroboy said:**
> But how do you make grub see the WinXP raid set, so that the user can choose at boot time which operating system to boot into?

Many thanks in advance.

I really have no idea... sorry. I'll have to think more about it, or someone else already has a solution.

---

### Post by fjgaude on 2007-10-12
> **DraK said:**
> Trouble I am having is that Linux says it does not have an NTFS partition...

Any ideas?

dmraid see's the raid, it is active and both drives are listed to.

You have to mount the Sil array by using dmraid, as shown earlier in this thread. You mount like so:

```
sudo mount -t ntfs-3g /dev/mapper/sil_ahahbhbjaddg /raid
```

You have had to created the mount point first with:

```
sudo mkdir /raid
```

You can create any mount point, e.g., /media/raid   or /media/winxp etc. that you wish.

Of course you have also had to have ntfs-3g installed. It is in Synaptic search.

---

