---
title: "Wine: drives not there!"
date: 2007-04-29
forum: General Help
---

### Post by Robbyx on 2007-04-29
I installed a program using wine and it runs. It needs to access a file with all my records in it. It is on drive f: in windows. Under  wine the program is only showing a restricted number of drives when I try to find the file. The drive with the needed file is not showing. I need to access the drive but do not know how to. I have tried the wine config program but it will not show the missing drives when I open the browse window.


How do I configure wine to see all the drives on my  workstation. I am running feisty.

I can see al the drives using ubuntu places.

---

### Post by Cryophallion on 2007-04-29
Is the drive mounted in Feisty?
If so, if you keep going up a folder in the select folder dialog, you will get to the root, where you can go to /media or /mnt to find the drive.

---

### Post by lukew on 2007-04-29
> **Robbyx said:**
> I installed a program using wine and it runs. It needs to access a file with all my records in it. It is on drive f: in windows. Under  wine the program is only showing a restricted number of drives when I try to find the file. The drive with the needed file is not showing. I need to access the drive but do not know how to. I have tried the wine config program but it will not show the missing drives when I open the browse window.


How do I configure wine to see all the drives on my  workstation. I am running feisty.

I can see al the drives using ubuntu places.

This is how i add my cdrom into wine:

```

cd ~/.wine/dosdevices
ln -s /media/cdrom d:
```


... however I did notice that in the version I am using there is a autodetect button under the drives tab of winecfg.

Luke

---

### Post by hyperair on 2007-04-29
Easiest way for teh n00bs ^^: Go to the run dialog and type winecfg. Then go look for drives and add them there. I think it's pretty straight forward.

---

### Post by arkiedan on 2007-04-29
> **hyperair said:**
> Easiest way for teh n00bs ^^: Go to the run dialog and type winecfg. Then go look for drives and add them there. I think it's pretty straight forward.

Easy for you - for me difficult. 

Winecfg is the strangest-looking application I've seen since I started playing with Linux (well, just a week ago, actually). The first time I used it I hit autodetect and it seemed to work. However, when I open XNView (or any app for that matter) under Wine I get this long string of drives that I've got to slowly hunt through to find my original C-Windows drive and Image directory. Tedious!

Is there another configuration application that'll simplify the Wine setup process? So far, for me at least, it's far easier to reboot back over the Windows XP (exactly what I'm trying hard to eliminate!).

So far, not enamoured with Wine. Accustomed to Windows XP so I find the interfaces of working applications ugly in the extreme. Takes me back to the early days of Windows.

Not a knock on Linux! I'll get there but it's a tough learning curve, especially for a seventy year old guy.

arkiedan

---

### Post by hyperair on 2007-04-29
Ah, after you autodetect, you figure out which drives you need and remove the rest? That works for me. You can figure out which drive letter maps to what by right clicking on each drive  in Places->Computer, and clicking properties, then going to the volume tab and looking at what is written for the mount point.

Also if you don't really like the theme in wine, you can look for a theme online, download it (it should be in the msstyles format, meaning the filename is something like something.msstyles) Then install it via winecfg in the desktop integration section. An example is this theme: [http://www.istartedsomething.com/20061029/royale-noir/](http://www.istartedsomething.com/20061029/royale-noir/), with the download link at the bottom. It's in an archive so you'll have to extract it though. Ubuntu's archive manager should handle it with the addition of the "rar" and "unrar" packages (installable from Synaptic Package Manager)


p.s. You are quite tech savvy for a 70 year old eh, not many others are like you. Good luck :)

---

### Post by Robbyx on 2007-04-30
I have tried to follow the advice but not all my windows drives are showing under \media. They appear under places but not within Wine. The other problem that may be related is that I found that when I wanted to save a file to  windows 2k  "my docs" folder it was reported to be read only.

---

### Post by lukew on 2007-04-30
> **Robbyx said:**
> I have tried to follow the advice but not all my windows drives are showing under \media. They appear under places but not within Wine. The other problem that may be related is that I found that when I wanted to save a file to  windows 2k  "my docs" folder it was reported to be read only.

Presumably you can see your windows files wihtin linux. what is the filesystem type? 

If it is fat/fat32 and is mounted as vfat and you need to check your fstab to ensure that it is not getting mounted as readonly. If you are not then it could be that there are errors on the disk and it is switching the file system to readonly. You will need to run fsck to fix these or change your fstab options.

If it is NTFS then you need to look into mounting ntfs from linux.

Luke

---

### Post by hyperair on 2007-04-30
If I'm not mistaken the drive is probably an NTFS drive. Could you right click on the drive in Computer and move to the Volume tab and then check the file system? If that is an NTFS drive, the folder is marked read-only because NTFS is a proprietary file system and write support is not supported fully by the NTFS drivers that are bundled with Ubuntu. Try installing ntfs-3g. 

```

sudo apt-get install ntfs-3g ntfs-config && sudo ntfs-config

```

EDIT: just edited the code above. Sorry for the error. I should practice my bash code more heheh.

---

### Post by Robbyx on 2007-04-30
> **hyperair said:**
> If I'm not mistaken the drive is probably an NTFS drive. Could you right click on the drive in Computer and move to the Volume tab and then check the file system? If that is an NTFS drive, the folder is marked read-only because NTFS is a proprietary file system and write support is not supported fully by the NTFS drivers that are bundled with Ubuntu. Try installing ntfs-3g. 

```

sudo apt-get install ntfs-3g ntfs-config && ntfs-config

```

Thanks for the replies. 

The above quoted went wrong. At the end of the installation it error'd that it could only be installed as a root. That should not happen if I am using sudo!  I then went off to synaptic and  reinstalled the ntfs-3g group that was showing as already installed in the first attempt. There was no problem with the installation via synatptic but when I went to check the drives in places computer,  I had to mount the drive and then found that the permissions could not be changed when I tried to change them from read only to read and write.  

How should I change the properties?

---

### Post by Robbyx on 2007-04-30
I found another way to mount and read windows / ntfs  drives that makes it much easier .

For others who may search for the truth after me here is a great solution:

[http://ubuntuforums.org/attachment.php?attachmentid=31316&d=1177940804](http://ubuntuforums.org/attachment.php?attachmentid=31316&d=1177940804)

---

### Post by Robbyx on 2007-04-30
Now that I have properly mounted the ntfs drives and made them w/r I can see them within winecfg.  I would like to remap the letters of some of the drives. Is it possible?

---

### Post by hyperair on 2007-05-01
I'd like to just warn you, that Automatix is a program that is not recommended by the Ubuntu team. Read this link for more info: [http://en.wikipedia.org/wiki/Automatix_%28software%29#Response](http://en.wikipedia.org/wiki/Automatix_%28software%29#Response)

Anyway, I edited my code in my previous post. Sorry for the inconvenience. Here it is anyway:
```

sudo apt-get install ntfs-3g ntfs-config && sudo ntfs-config

```

or if you have installed it already:
```

sudo ntfs-config

```

---

### Post by arkiedan on 2007-05-01
> **hyperair said:**
> Ah, after you autodetect, you figure out which drives you need and remove the rest? That works for me. You can figure out which drive letter maps to what by right clicking on each drive  in Places->Computer, and clicking properties, then going to the volume tab and looking at what is written for the mount point.

Also if you don't really like the theme in wine, you can look for a theme online, download it (it should be in the msstyles format, meaning the filename is something like something.msstyles) Then install it via winecfg in the desktop integration section. An example is this theme: [http://www.istartedsomething.com/20061029/royale-noir/](http://www.istartedsomething.com/20061029/royale-noir/), with the download link at the bottom. It's in an archive so you'll have to extract it though. Ubuntu's archive manager should handle it with the addition of the "rar" and "unrar" packages (installable from Synaptic Package Manager)


p.s. You are quite tech savvy for a 70 year old eh, not many others are like you. Good luck :)

Good stuff! Thanks! I think I can handle this now. I like the idea of changing themes and I'll certainly do that.

As for not many others like me? Yeah, and I mourn their passing every day. 

Thanks again. I'm getting there.

arkiedan

---

