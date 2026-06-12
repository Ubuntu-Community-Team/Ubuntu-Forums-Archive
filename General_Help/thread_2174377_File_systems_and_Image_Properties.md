---
title: "File systems and Image Properties"
date: 2013-09-14
forum: General Help
---

### Post by kunaguvarun on 2013-09-14
[COLOR=#333333][FONT=UbuntuRegular]The other day I went to print my photograph from USB drive. The image is a JPEG file. I copied it to the USB drive which was formatted in FAT-32 format. I didn't realized this and proceeded with the copying. The target is a Windows machine. I was surprised to know that the windows machine was unable to recognize my photo(JPEG) which is well usable in my Ubuntu box.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I returned home and later did the same copy operation in Windows OS which I was dual dual booting with Ubuntu. Voila!!! Windows cautioned me "Do you want to copy the file without its properties?". I was pleased to know that at least windows prompts this message. I later formatted my pen drive to NTFS and things are fine. I'm not sure how the copy operation would result in Ubuntu with NTFS as the option.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm guessing that the copied file (My JPEG based photo) would still be usable and recognizable if the target PC is a Linux...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My question is how to prevent such awkward situations while still using Linux(ubuntu)? How to know beforehand that these situations might arise?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks in advance[/FONT][/COLOR]

---

### Post by mcduck on 2013-09-14
Did you safely remove the drive after copying the image to it, or did you just unplug it?

There is nothing on FAT filesystem that would cause issues with JPEG images on it, your picture should be perfectly fine (unless it's size is larger than 4GB, which is the maximum filesize limit on FAT).

The "properties" that can't be copied are things like file ownership and permissions, and not having them will not break the image file in any way.

---

### Post by kunaguvarun on 2013-09-14
I hit Eject option. I'm sure that I didn't unplugged it. The file size is 150KB. Windows was able to prompt that the file would be copied without any properties. I just want to know why is mo such thing available in ubuntu ?

---

### Post by ajgreeny on 2013-09-14
I have never seen this situation before, but let's check a few things.

Can you go to your ubuntu system and run the following command on the original jpeg file that you copied to check if there is anything unusual about that file, eg, is it a real jpg or perhaps another filetype just given the jpeg suffix by mistake in some way or other.
```
file /path/to/file/jpeg
```

---

### Post by mcduck on 2013-09-14
> **kunaguvarun said:**
> Windows was able to prompt that the file would be copied without any properties. I just want to know why is mo such thing available in ubuntu ? 

Like I said, the properties not being copied is not the reason for your image file not working, something else must have caused it to not copy correctly.

The properties are just additional information the filesystems save about files, and are rarely any importance when moving the file to another system, and have absolutely nothing to do when it comes to the contents of the file.

---

### Post by CeejRab on 2013-09-14
Hello K[[COLOR=#000000]unaguvarun[/COLOR]]("http://ubuntuforums.org/member.php?u=1845090"),

Your incident here is rather intriguing, ive never heard of it before in all my years of computing on many different operating systems....

Going by what the others have said and from your information you provided, it sounds like either the image itself is corrupted, or else im clueless! The type of filesystems doesnt ususally alter a file's makeup. A JPEG image can be placed from an EXT-3 partition to an NTFS, FAT, FAT-32, EX-FAT, or EXT-4 partition without losing the stability of the file. 

Were you using windows 7 by any chance? I was dual booting W7 and Ubuntu 12.04LTS recently and found that when i copied a file to my usb drive it asked me the same thing, if i wanted to proceed copying the file without its properties.... I dont think i quite understand it but i formatted the USB drive as FAT-32 and rebooted the system, and i havent gotten the same message again since. I'd say format the drive and make sure your images arent encrypted or currpted, and you shouldn't get the same problem again. 

Hope this was of some help, 

-Christian

---

### Post by kunaguvarun on 2013-09-15
@[[COLOR=#000000]ajgreeny[/COLOR]]("http://ubuntuforums.org/member.php?u=27747")[COLOR=#000000] ,

Here is the output of the command you asked me to execute
[/COLOR]
> varun@varun-G31M-ES2L:~$ file /media/win_d/PHOTOS/IMG_5232\ \(\ 197474\ \).jpg [COLOR=#000000]
[/COLOR]/media/win_d/PHOTOS/IMG_5232 ( 197474 ).jpg: JPEG image data, JFIF standard 1.02
[COLOR=#000000]

[/COLOR][COLOR=#DD4814][COLOR=#000000]@[Christian_Rabideau]("http://ubuntuforums.org/member.php?u=1860756")
[/COLOR][/COLOR][COLOR=#000000]
 [/COLOR]
[COLOR=#000000]Hi, Thanks a lot for your reply. I'm dual booting with Windows 7. The initial format of my USB drive is actually FAT-32. Copy operation in Ubuntu : Copied the file, but not usable/recognizable in Windows 
Copy operation in Windows : Prompted "Do you want to copy the file without its properties?" 

I formatted it to NTFS and then,

Windows : Copied successfully and usable in target windows PC.
Ubuntu : Not actually tried copying in NTFS.

My question, why does Ubuntu(Linux) copy operation didn't predicted the outcome?

Image is a perfect JPEG according to the previous output.[/COLOR]

---

### Post by CeejRab on 2013-09-15
Not exactly sure why the properties data wouldnt be carried over in the first place, nor why windows gives an alert about it. I think you'll find that only windows 7 gives that alert, because i never saw or heard of it until i dual booted win7 and ubuntu. 

The big thing is, your image isnt losing its value integrity by being transferred.

On another note, what kind of properties is it referring to? Like, the tags and watermarks and camera information that the camera places into a image file? I dont see why those wouldnt be transferred properly, but heres an idea...

In other instances somewhat similar to this, it helps if you transport things in an archive. Download 7zip in ubuntu (sudo apt-get install 7zip) or via the software center, and also in windows. Use 7 zip to make a simple zip archive with your files that you desire to transport to the other OS. When you extract the zip folder on the other os, all should be well, if my theory is correct! Let me know how it goes if you try!

---

### Post by kunaguvarun on 2013-09-16
@[**[COLOR=#000000]Christian_Rabideau[/COLOR]**]("http://ubuntuforums.org/member.php?u=1860756"),
Zipping file makes sense. Will try it out

---

