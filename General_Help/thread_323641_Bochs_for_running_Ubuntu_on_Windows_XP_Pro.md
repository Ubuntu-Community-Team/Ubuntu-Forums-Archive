---
title: "Bochs for running Ubuntu on Windows XP Pro"
date: 2006-12-22
forum: General Help
---

### Post by rzs on 2006-12-22
Hi,
I recently got a Ubuntu Live CD and I would like to run it on top of Windows XP Pro. I downloaded Bochs 2.3 . I then created an iso image of the Ubuntu Live CD called ubuntucd.iso using WinImage,which I then placed in the Bochs directory which in my case is C:\Program Files\Bochs-2.3.My c:\ drive is of NTFS type.
I now need to modify bochsrc.txt but all the documentation Ive come across talks of modifying the floppya line.But since the iso image is of a CD not a floppy I dont know what exactly should be added to the bochsrc.txt file. 
I am new to Linux so I am really not sure of whether what im doing makes sense or not .So,I have the following two questions :
1) Will it be possible to boot Ubuntu on my XP box using the iso image of the Ubuntu Live CD that i have created ?
2) If it is possible then,what line do I use in the bochsrc.txt to make it work ?

Thanks a lot :)

---

### Post by sorlok_reaves on 2007-11-22
Apologies to drag up an old post, but I hate leaving a question un-answered.
Yes, the Ubuntu live CD should boot (although I quit halfway through loading, Bochs is unbearably slow even in loading Xubuntu).

You'll need the following lines somewhere in your bochsrc:

ata0-slave: type=cdrom, path=xubuntu.iso, status=inserted
boot: cdrom, disk

That's all; pretty easy. I know that Ubuntu works fine in VMWare (and _maybe_? in Plex86? Anyone?) You might want to try these; they're faster than Bochs, which emulates everything for the sake of compatibility.

Cheers!

---

