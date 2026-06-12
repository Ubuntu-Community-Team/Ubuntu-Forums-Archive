---
title: "Using NTFS 128GB Micro SD Card between Xubuntu and Windows XP = Data Write ERRORS!!"
date: 2022-04-17
forum: General Help
---

### Post by 777funk on 2022-04-17
I rarely use Windows anymore but I still need it on my music recording laptop. I have XP on that machine and it does everything I need to produce music (synths, good fast I/O for analog signal, good effects, etc) so I will not be moving on from XP until that laptop breaks and if it does I may replace with the same Lenovo unit. It's just a good system.

But that said, I'm having LOTS of trouble with data. I was originally writing to a 128GB sandisk SD card while recording but I noticed in one project that the files were not written. Thankfully my DAW doing the recording still somehow was able to play the files back. I don't know how since they're not on the SD.

But that said, does anyone know why this would be? 

Similarly, sometimes I will put files on the card in Win XP and they're not there when I load it into my Linux machine. I've noticed this with multiple SD cards so it's not the card that's the issue. 

The cards were formated in GParted and to NTFS for what it's worth. Maybe I need to format within Windows XP instead??

---

### Post by TheFu on 2022-04-17
Xubuntu 18.04 support ended a year ago. [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/)

I cannot help with WinXP. Too old for me to remember all the tiny little things that it lacks. I do know that over the years, NTFS has been silently upgraded by MSFT.  I wouldn't use NTFS on any flash media - in general it is smarter to avoid any journalling file system on flash media.  But the file systems I'd use today on flash media (exFAT or f2fs) probably aren't supported by XP.

Not everything lasts for ever. Over 20 yrs is a very long time for any OS release.

---

### Post by 777funk on 2022-04-17
> **TheFu said:**
> Xubuntu 18.04 support ended a year ago. [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/)

I cannot help with WinXP. Too old for me to remember all the tiny little things that it lacks. I do know that over the years, NTFS has been silently upgraded by MSFT.  I wouldn't use NTFS on any flash media - in general it is smarter to avoid any journalling file system on flash media.  But the file systems I'd use today on flash media (exFAT or f2fs) probably aren't supported by XP.

Not everything lasts for ever. Over 20 yrs is a very long time for any OS release.

I need to update my sig line. This is on 20.04.

---

### Post by oldfred on 2022-04-17
I do not do music production, but remember (amazing for oldfred) that a user posted that once he converted to Linux it was much better. 
But a learning curve as not same tools.

Google first page had this:
> **Linux distro is considered a good choice for any user**  because it offers many more benefits, DAW (Digital Audio Workstation),  manipulation tools, countless image editors, etc. Users can use these  distros in detail by crossing their creative limits while sitting  comfortably.

---

### Post by tea for one on 2022-04-17
> **777funk said:**
> Similarly,sometimes I will put files on the card in Win XP and they're not there when I load it into my Linux machine. I've noticed this with multiple SD cards so it's not the card that's the issue. 
It may not be the SD cards but the issue may be an unsupported OS (i.e.Windows XP) not writing the data correctly to the SD cards.

Boot into Xubuntu and write some data to the SD cards.
Reboot into Xubuntu and see if it is visible?

---

### Post by bobunderwood99 on 2022-04-17
Consider adding support for exFAT to XP. **Proceed at your own risk!**

[http://greyghost.mooo.com/windows-exfat/](http://greyghost.mooo.com/windows-exfat/)

---

### Post by vanadium on 2022-04-18
I expect your file system may not be healthy. A healthy ntfs file system should interchange properly between linux and even an old Windows XP system. Make sure to check and repair the ntfs file system in Windows XP. Make sure to always correctly unplug the SD card. Keep the habit of periodically checking the file system.

---

### Post by TheFu on 2022-04-18
I've had NTFS file systems become corrupted by a video recording HW device.  The only solution was to reformat it and lose all the data.  That device only supports either NTFS or FAT32, so there isn't much choice for which to be used. NTFS is the better choice.  BTW, in a Windows computer, NTFS seems to be very, very stable, but I wouldn't use it on any flash storage, like an SD card.

---

