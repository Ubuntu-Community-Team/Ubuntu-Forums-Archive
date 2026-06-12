---
title: "[SOLVED] Escape From FAT32"
date: 2008-05-29
forum: General Help
---

### Post by ILYA99 on 2008-05-29
Hi I got FAT32 formatted HD mounted to XUBUNTU.
I want to migrate to file system that
[LIST=1]
[*]Supports large files
[*]Can be used with MS Windows
[*]Data losseless convertion
[/LIST]

Thanks

---

### Post by forestpixie on 2008-05-29
You can change fat32 to ntfs, I believe that data is as safe as it ever is doing partiton operations.

[http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

Bear in mind ntfs is only recognised afaik by win2k, xp and vista.

Also that the entry in fstab  will need to be amended.

---

### Post by ILYA99 on 2008-05-29
> **forestpixie said:**
> You can change fat32 to ntfs, I believe that data is as safe as it ever is doing partiton operations.

[http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

Bear in mind ntfs is only recognised afaik by win2k, xp and vista.

Also that the entry in fstab  will need to be amended.

That means i have to attach the HD to Windows XP machine ?

---

### Post by edd07 on 2008-05-29
> **ILYA99 said:**
> That means i have to attach the HD to Windows XP machine ?
No, Xubuntu will be able to read it too, and if you have a recent version, to write to it also.

You could use ext3 as well, its the file system that Ubuntu uses by default. Windows can't read it natively, but you can install a driver and it'll work. You can download it from [www.fs-driver.org]("http://www.fs-driver.org") But I don't know if you're going to be able to convert FAT32 to Ext3 without any data loss.

Hope this helps

---

### Post by ILYA99 on 2008-05-29
> **edd07 said:**
> No, Xubuntu will be able to read it too, and if you have a recent version, to write to it also.

You could use ext3 as well, its the file system that Ubuntu uses by default. Windows can't read it natively, but you can install a driver and it'll work. You can download it from [www.fs-driver.org]("http://www.fs-driver.org")

Hope this helps

Thanks it helps alot. 
Just one more thing:
How can i convert this HD to ext3 ? Do I have to format ?

---

### Post by kaiju on 2008-05-29
well, if you really need windows support, fat and ntfs are pretty much the only options, and only ntfs supports large files. i think you'll have to use windows for the conversion (partition magic is good for that).
on the other hand, i think i've read somewhere that it is possible to make windows 'recognize' ext3, so if you'd rather like a filesystem better and faster than the ms-natives, you could google around for that.

[edit:]

oh, late :P

to convert, you can back up everything on your fat partition and then format it as ext (as edd07 already said, it won't go without data loss).

---

### Post by danwood76 on 2008-05-29
Just convert it to ntfs.
ext3 driver in XP is shabby at best, ntfs-3g is far better.

I have a 1TB drive formatted NTFS which I use to store all my video data that I use in both OS's (sharing with Vista) and have never had any issues.
NTFS-3G is really good with ntfs, like I said I've had no issues.

---

### Post by edd07 on 2008-05-29
> **ILYA99 said:**
> How can i convert this HD to ext3 ? Do I have to format ?
You can format with GParted, wih comes with every Ubuntu LiveCD. And, yes, I believe you have to format.

> **kaiju said:**
> i think i've read somewhere that it is possible to make windows 'recognize' ext3, so if you'd rather like a filesystem better and faster than the ms-natives, you could google around for that.
Yeah, the software from the link I provided does exactly that ;-). It gives both read and write access. I have installed it in XP and Vista, and works perfectly in both. To install in Vista you have to enable compatibility mode, though.

EDIT: Oops, I was late too, :-P

Good luck

---

### Post by ILYA99 on 2008-05-29
Thanks guys ! 
Ill do some thinking wich one is best for me - 
backup & format or detach and convert on another machine.

---

### Post by forestpixie on 2008-05-29
I would agree with those that have recommended the ntfs tools, I have read of problems with access rights - it doesn't maintain them - read the ext2 ifs faq.

ASsuming that you can accessa win machine there should be no data loss problems changing from fat32 to ntfs - I've done it myself with no problems.

---

