---
title: "Ubuntu only at the moment... Want to dualboot with Windows 8."
date: 2013-08-20
forum: General Help
---

### Post by Styleion on 2013-08-20
Hi people,

I've got a Sony Vaio S15 laptop (UEFI) with Ubuntu only on it and I decided I want to install Windows 8 and dualboot both operating systems.
What's the best and safest way of doing this? I understand I have to repartition the disk to make space available for the Windows 8 installation... Should I use UEFI or legacy? Parted or fdisk? What happens with GRUB?

I've looked it up on the forums and googled it but I'm pretty confused.

---

### Post by sioxs on 2013-08-20
Multi-boot systems are fairly straight forward today: 
In the case of a Windows installation AFTER Linux is installed you will have to force a re-installation of the Linux boot loader in order to use Linux again. This is due in part to a number of bugs within the architecture of Windows. see man "fdisk" - DOS partition table section for a example
Restoring the MBR can easily be accomplished with a Live disk like "rescatux" "systemrescue" or "SDG" etc. 
So your first order of business should be to get a live distribution and familiarize yourself with it before doing anything drastic.
**It is always recommended to let different platform OS's you want to install format it's own root partition. (especially Windows)
For Questions regarding dual booting + installation tips see: [URL="http://askubuntu.com/search?q=Dual+boot+Linux+Windows+"]AskUbuntu
[/URL]
Don't forget to make a backup in case anything goes wrong by using a tool like "partimage" to clone the OS's partition to a separate media device. 
Then you can make space where the new OS will reside. 
Followed by formatting your drive with your Windows installation media.
Once the installation is complete, reboot to ensure it's working as expected.
Finally run the Live Disk (described above) to restore Grub.
Everything should work with the new OS added to the grubs menu list.

PS. you do know Windows 8 is meant for touch screens right?

Peace
sioxs

---

### Post by Crusty Old Fart on 2013-08-20
You may have a better chance of success if you back up everything you want to keep from your Ubuntu installation. Zero write your drives. Install Windows first and perform your partitioning during installation. And then install Ubuntu. Windows can get really fussy, even nasty, if it isn't installed as the first OS. It doesn't tend to play very nicely if it doesn't have the whole computer to itself when it's installed.

---

### Post by sioxs on 2013-08-20
> **Crusty Old Fart said:**
>  Windows can get really fussy, even nasty, if it isn't installed as the first OS. It doesn't tend play very nicely if it doesn't have the whole computer to itself when it's installed.
That's pretty much what I was alluding to, although it isn't necessary to destroy what you have.
Windows can't read ext2-3-4 and many of the other formats Linux supports so as long as your conscientious about "where" on the drive windows will install you shouldn't have to worry too much except to restore the MBR to what it was doing before Windows took over the system.

---

### Post by Crusty Old Fart on 2013-08-20
> **sioxs said:**
> That's pretty much what I was alluding to, although it isn't necessary to destroy what you have.
Windows can't read ext2-3-4 and many of the other formats Linux supports so as long as your conscientious about "where" on the drive windows will install you shouldn't have to worry too much except to restore the MBR to what it was doing before Windows took over the system.

Yup. I'm not disagreeing with your guidance. Just wanted to make the point unmistakeably obvious. Installing Windows first, on clean drives, may be a much easier way to go, especially if the Ubuntu OS that's presently installed is a recent enough installation that it can be "thrown away" and reinstalled last without any significant loss.

---

### Post by sioxs on 2013-08-20
> **Crusty Old Fart said:**
> Yup. I'm not disagreeing with your guidance. Just wanted to make the point unmistakeably obvious. Installing Windows first, on clean drives, may be a much easier way to go, especially if the Ubuntu OS that's presently installed is a recent enough installation that it can be "thrown away" and reinstalled last without any significant loss.

Exactly; I actually thought about including that as I wrote but opted to throw in partimage as a solution for those who might me unfamiliar with it.
Personally I can't count how many times that command line program has saved the day.

---

### Post by Crusty Old Fart on 2013-08-20
This may be a big help: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

