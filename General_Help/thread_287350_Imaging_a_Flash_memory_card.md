---
title: "Imaging a Flash memory card"
date: 2006-10-28
forum: General Help
---

### Post by Warwick on 2006-10-28
Background: I had my camera stolen on Monday. The police recovered it for me and charged the thief so I'm happy. The day before it was stolen I uploaded all the pictures I wanted to my PC so no data lost even if I hadn't got the camera back.

The minor problem: Some of the pictures that were on the CF card are no longer there. This indicates that the thief deleted them and opens the possibility that he also took some. I'd like to see them. I'm aware that there are few to no file recovery tools for Linux but I do have them at work on my 'doze box. The 'doze box software is perfectly happy to deal with bit image files such as Winimage and has successfully recoved from such before. 

Is there any way I can create such a file from Ubuntu? If I can make the file, I can upload it and access my PC via RDP over the VPN.

---

### Post by Warwick on 2006-10-29
Hell. It'll wait. I just got back from hospital after having the cr*p beaten out of me instead.

---

### Post by GordSellar on 2007-03-13
Did you ever figure out a way to do this? I'm just curious. 

Hope things are going better for you!

---

### Post by GordSellar on 2007-03-13
By the way, I once successfully used some free app or other in Windows to recover deleted files on a screwed up card, but I don't know if there's anything to do the trick in Ubuntu... though I'd like to know if there were...

---

### Post by fragos on 2007-03-13
The file format on your CF card is Windows FAT.  You try taking a copy of the Windows undelete executable and run it on Ubuntu using wine.  No prediction on if it will work but it's worth a try.

---

### Post by peabody on 2007-03-13
I'm a command line guy, so this might not be the most user friendly solution, but dd can be used to image almost everything Linux can look at.

dd if=/dev/sda1 of=pen.vfat

You'll need to replace the /dev/sda1 portion above with the path to the particular device file for the CF reader.  That can vary.  My USB pen's device file is /dev/sda1.  Typing "df" in a console will give you a listing of mounted devices and their corresponding mount points in the file-system heirarchy.

---

### Post by flyingbrass on 2007-03-14
> I'm aware that there are few to no file recovery tools for Linux...

You could try this: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

