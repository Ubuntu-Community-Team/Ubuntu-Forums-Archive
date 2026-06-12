---
title: "Windows &lt;3's hijacking my MBR"
date: 2007-10-21
forum: General Help
---

### Post by Ryoushi19 on 2007-10-21
I like Ubuntu a lot better than Windows, but sometimes, there's just nothing better than Half Life 2, and wine hates me, since I run a crappy ATI Radeon 9200.  Hence, I still have a Windows partition.  The problem arises with the fact that whenever I boot windows, it "fixes" my MBR automatically.  That's a problem because by "fix" Microsoft means "hijack".  Every time I boot windows I have to restore my MBR using a live CD, because it makes it so the MBR defaults to my Windows partition..  Is there some way to stop Windows from auto-"fixing" the MBR?  I'm running XP SP2.

---

### Post by Matticus on 2007-10-21
I have never heard of windows auto fixing the MBR, to fix the MBR myself I have always used partition table doctor.

Does the mbr need fixing before you actually boot into windows? In order to boot into windows you have to fix the mbr?

So I assume youve got grub installed and you click the windows partition then it flairs up some crud about fixing the MBR??

is the partition on a different physical drive to ubuntu? or the same drive? I ask this because on some other linux's I have had trouble booting a windows partition which is on another drive, this was fixed by changing the drive name from like hda or sda 0 to 1, linux seemed to detect the windows partition was somewhere it wasnt, but it never asked for mbr just wouldnt boot, so I dont know.

---

### Post by Ryoushi19 on 2007-10-21
The MBR does not "need" fixing, because I boot windows off of grub.  But after I boot windows, I have to change the mbr to boot linux.

Whenever I start windows, it says nothing, just silently fixes hda3 to be the boot drive.

They are both on the same hard drive on split partition.

---

### Post by sauf on 2007-10-24
How did you fix the MBR from the LiveCD?

I have the same problem, when I started HP Backup and Recovery Manager on my laptop.

System: HP Compaq 6510b, 2GB RAM, 160GB HD, 1440x900 14,1"

---

### Post by -Zeus- on 2007-10-24
I do a dual-boot and I don't have any problems... oh also, the problems with HL2 is nt due to the GPU probably, it's most likely due to the inherent natuer of instability when running win32 apps in ubuntu

---

### Post by fualad on 2007-10-24
I get the same behavior, but i run 2 HD's. 1 is IDE and the other is SATA. I can not find a way via bios to select one as master over the other. But which ever OS booted prior will be the dominate OS on the next boot.

---

