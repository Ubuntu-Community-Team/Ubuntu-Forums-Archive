---
title: "From NTFS to Fat32"
date: 2007-05-31
forum: General Help
---

### Post by reggierabbit on 2007-05-31
Hi, 

I recently installed the latest Kubuntu. My partitions are as follows:

Windows XP:NTFS 10gb
Data:NTFS 193gb
Kubuntu:EXT3 30gb
Swap:1gb 

Basically im screwed, i cant read and write files on my data partition from Kubuntu. Is there any way, i can somehow get the Data partition to Fat32 other than backing up and formatting.

I tried using Acronis and, resizing Data to 140gb, make the unalocated space as Fat32, copying program files to newly created partition, then resizing data again and copying more files to the fat32 partition etc. and then  merging the partitions to the new fat32 data partion.

But, i dont trust the program files, they wont work when moved. What if i change the fat32 letter to D:(which is the letter for data now).

Anyone know an easier method, or has anyone had to do the same thing, oh and btw, the data partition has 140gb used.

Thanks

---

### Post by Vajra Vrtti on 2007-05-31
If you are using Feisty (7.04) the package 'ntfs-config' will give you read/write access to your NTFS partitions.

---

### Post by reggierabbit on 2007-05-31
i installed the ntfs config, and ive had a look on websites on how to work it. I had to run it with command cause it wont work from menu. But on a website it comes up with these other options to name it and stuff. When i launch it , it just says, mount from external or internal device, i click internal, and thats all. The partition appears on the desktop with a weird name and no option to unmount like on the website. Am i doing evrything right?

---

### Post by Vajra Vrtti on 2007-05-31
All I did was to install ntfs-config and then activate the write support in 'System Tools -> NTFS Configuration Tool'. 
It remounted my NTFS drives in write mode and everything worked fine from then on.

---

### Post by Osiris* on 2007-05-31
If you want, since it sounds like your'e just starting out, you could use Automatix and install their read/write ntfs software.  Works like a charm for me.  After install, I rebooted, and my NTFS was mounted with no problems writing to it.

---

