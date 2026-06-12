---
title: "Dual boot on SSD (Ubuntu+Win8)"
date: 2014-09-26
forum: General Help
---

### Post by Orion_PKFD on 2014-09-26
Hi folks,

I was wondering if anyone can help me out with the following:
I  am buying and Asus N550JK, but it comes with a 750GB HDD. I was  thinking about substituting this HDD to a 512GB SDD (Samsung PRO) since  it faster.
The laptop comes with Win8 installed, but I will install  Ubuntu as dual boot (actually, I'll use Ubuntu >90% of the time; I  need Win8 only for some programs which I have troubles to run in  Ubuntu).

My questions are:

i) Is there any disadvantage to partitionate an SDD (I am kinda noob on this matter) for dual-boot?
ii) Is it safe to rely on the SDD alone?

It would be most helpful to answer to this question (or to highlight any other thing that you may think relevant).

Cheers!

---

### Post by weatherman2 on 2014-09-26
Yes, you can dual boot Ubuntu and Windows 8.  I am doing it on this computer. Sometimes the secure boot (UEFI) causes issues in installing Ubuntu.  On my laptop, Grub can't boot Windows 8 from the menu - I get an error, but I can hit the F12 key to get a BIOS boot menu and boot Windows 8 that way so not much of an issue.  Be prepared to run Ubuntu "boot repair" after your initial installation in case it doesn't quite work, but you can do that from a live USB boot.  Maybe it will be easier now.  I installed Ubuntu 12.04.2 originally.

Are SSDs as reliable as hard drives?  Probably more reliable, as your SSD has no moving parts, but you should never rely completely on any storage device never to fail.  SSDs fail too.  You still need to make backups whether you use an SSD or HDD.  I love my laptops SSD.  I wouldn't have any fear about using one.  But I still make backups at least occasionally and always when I know I would lose important files if my SSD failed (so after I download my vacation photos, I make an immediate backup elsewhere).

What I would probably do is clone your HDD to the SSD, then keep the HDD as a backup. (I would do the same even if you were getting a new HDD instead of an SSD.)  I use Clonezilla to clone Windows 8 systems and it works fine, but you will need to shrink the larger partition first on the larger 750GB hard drive so that it can "fit" when you clone to the SSD.  Assuming your laptop is brand new, the 750GB drive should be almost empty so shrinking the WIndows 8 partition should be quick and easy.  I would shrink it as small as you want it on the final SSD.  Say you want 100GB for Ubuntu.  Then shrink the 750GB Windows partition (or whatever approximate size it is) to say 350GB to 400GB.  Then clone to the SSD.  You'll have free space left over on the SSD, and you can install Ubuntu in that.

---

### Post by Orion_PKFD on 2014-09-29
So, there is no problem in duall booting (Win8+Ubuntu) on a SSD?
Even not having a "physical" partition?
Will the partitioning affect SSD's lifespan?

Cheers

---

### Post by d4m1r on 2014-09-29
No, there should be no problems dual booting any version of Windows with any version of Ubuntu on an SSD.

And no, having multiple partitions does not affect a harddrives (even an SSDs) lifespan.

Are you planning on cloning all your data/OS/partitions from the standard HDD to the SSD or just starting clean? I would recommend the later option so you don't have to deal with cloning software which is very hit and miss I have found over the years. Also, in that case and despite what anyone tells you, install Windows first always....Ubuntu is smart enough to recognize any other OS' on the machine during its installation, Windows is often not.

---

### Post by oldfred on 2014-09-29
Some other Asus installs. Should be similar whether hard drive or SSD.

 Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
      
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

