---
title: "Ubuntu 7.10 :- how to Hide folders + Issues with Sound"
date: 2007-11-13
forum: General Help
---

### Post by Cliff885 on 2007-11-13
Hello there!

A TOTAL newbee here !

I'm glad to joing the Linux/Ubuntu Community ! :)

Hope this is going to be a very educational experience. The only other OS i've used is Windows ! :/   *shame* 

Anyway, I shall keep things short and sweet, so that somebody can help me.

I am Dual-booting Ubuntu 7.10 with Windows XP.
Everything is working fine in terms of booting etc.
Except:

**_PROBLEMS:_**

[LIST=1]
[*]**I cant get any Audio output while using Ubuntu 7.10 (Sound is ok in Windows XP!)**
[*]I want to know how to "Hide" or "LOCK" Folders in Ubuntu 7.10, like it is possible Windows, to hide and/ password-protect folders Eg: by using a program like "FolderLock" ?!
[/LIST]

**_(1)_**
Having read a few related threads.. I realise that the following information might be helpful to whoever is out there who could help me.
(PLEASE let me know if you need any more information, and if so..HOW to obtain it?! ;) )

This is what I get from "alsamixer"
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC882                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Headphone                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;             &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9492;&#9472;&#9472;&#9496;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;           100<>100   81<>81   42<>42    0<>0        0        0      0<>0     &#9474;
&#9474; <Headphon>  PCM      Front   Front Mi Surround   Center    LFE      Side     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

And
this is the output I got from the "lspci" command:
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:03.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: nVidia Corporation NV42 [GeForce 6800 XT] (rev a2)
```

Also a Screen shot of:** "System>Preferences>Sound"**
[IMG]http://img232.imageshack.us/img232/2094/screenshotsoundpreferenmg9.png[/IMG]

What am I doing wrong????

**_(2)_**
**I would like to know how to Lock Folders in Ubuntu 7.10** like it is possible in Windows by using a software like "Folder Lock"
Either password protect and/or hide from other users etc...?

"Folder Lock" works like charm for me in Windows.
So just looking for the equivalent in Linux?!

I have heard that you can RENAME the files with a period '.' at the beginning of a file or folder so that it becomes a "Hidden" file/folder.
OR
create a file called ".hidden" in the same directory level as the files/folders  that you want to hide are in, and in the file define the NAME for each of the files/folders that you want to "hide", one per each line.

Now, both of these methods work.
But it only "Hides" the files/folders.

As soon as you hit "Ctrl+H" 
anybody can have access to any of these "Hidden" files.
(assuming that somebody has already logged in under my own account.)

So any OTHER way to do it... as in windows.. and I say again.. if anybody knows about "Folder Lock" and how it works..?!
That is exactly the functionality that I am looking for in Linux?!
 

Any help would me much appreciated!
Thank you in advance!

Cliff

---

### Post by renzokuken on 2007-11-13
your sound card is covered in several threads already i think. need to add snd=hda_intel or something to alsaconf.

as for hiding folders.....simply put a "." in front of the name, i.e.

Folder     -     visible

.Folder   -    invisible

EDIT: should have finished reading your post.....sorry

---

### Post by JasonF on 2007-11-13
To hide a folder you could try using something like 'truecrypt' (google it) to create an encrypted volume, and mount it when required. Alternatively, just don't let other people use your user name, and make sure the directories permissions don't allow anyone else in (Though this won't protect you from root).

---

### Post by geirha on 2007-11-13
Not sure what locking a directory is supposed to do other than preventing access, but you could prevent access by doing something like ```
sudo chmod 000 the_dir
``` which simply removes all permissions on the directory, making it only accessible by root. ```
sudo chmod 755 the_dir
``` will "unlock" it, giving everyone read access, and the owner read/write access.

---

