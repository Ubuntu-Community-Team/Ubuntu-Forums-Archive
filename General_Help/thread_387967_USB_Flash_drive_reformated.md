---
title: "USB Flash drive reformated?"
date: 2007-03-18
forum: General Help
---

### Post by Dr Small on 2007-03-18
I have a USB2.0 2GB Flash Drive, and I use it for copying files back and forth from my dualboot of Windows XP and Ubuntu Systems, and it has worked great up until today.

I have pictures, documents, and programs all on this thing, and Windows reads it fine. Ubuntu does also. But today, I tried copying an image from Windows onto the USB and the booted back up in Ubuntu and found the file unreadable. I took it to another Windows XP computer, and it was still unreadable. 

I booted back up in Windows, and it was unreadable, yet the original file on the computer was readable. So, I tried this same operation several times, and it still proved the same thing.

So, this time, while on Windows, I placed the image on the USB, removed the USB, then reinserted it in. Browsed to the USB and found the image unreadable, JUST AFTER I HAD PLACED IT ON IT! 
So know I think it's a problem with the USB. I'm all upset, so I reboot in Ubuntu to try something else.

I placed another picture on the USB, ejected it, reinserted it, and then found that the picture IS readable. So, it must be something with the USB, and it acts like it has been formatted only for Ubuntu or something.

I have not reformatted the thing or anything, and it only happened today, so I have no clue what the problem could be.

If anyone smarter than me understands what is going on here, and if they could lend me a hand, I would greatly appreciate it.

PS> I did try several different images and text files on the Windows computer, but all of them proved the same results of the files being corrupted upon ejection of the USB from the computer.


Dr Small

---

### Post by dcstar on 2007-03-18
> **Dr Small said:**
> 
.........
PS> I did try several different images and text files on the Windows computer, but all of them proved the same results of the files being corrupted upon ejection of the USB from the computer.

Dr Small

One hopes you are using the "Eject" command in Windows, which must complete 100% to write any cached file and directory data to the USB stick **before** removing it.

Large files can take a long time to write to a USB stick, just because the Windows program indicates that the copy has completed does not mean the data has been written to the device, cached data is written in background mode and this can take time.

People just unplugging USB devices experience the sort of file corruption you have described.

---

