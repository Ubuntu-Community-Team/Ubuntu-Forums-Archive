---
title: "Deleting in Linux altogether (Ubuntu File System)"
date: 2014-04-06
forum: General Help
---

### Post by Jason_Minns on 2014-04-06
My question stems from usb drive transfers between Linux and Windows 8. I started putting a file on a usb drive, and then saw that it was a file that I had already tranfered, so I deleted it off the usb thumb drive. When I opened the thumb drive in Windows 8, I saw that the file, while seemingly was deleted in Linux, showed as a trash file in Windows, and therefore took up space. 

With that being said, If I use the graphical interface in Linux Ubuntu in the file location, for example /home/videos, and I delete a video, is the same thing happening? And, is there a better or more propper way of deleting or ridding files in the Linux file system? Is this also something I would have to update the data base upon deletion?

Thank you, Jason

---

### Post by timgood on 2014-04-06
I seem to recall that holding down the shift key while pressing 'delete' will delete files rather than moving them to the trash. Try it.

---

### Post by Jason_Minns on 2014-04-06
Yeah, cause afterwards I'd have to go into the usb drive, /media/sdb1 and with the terminal use the command: 
sudo rm -rf .Trash-1000/
I guess I was just wondering if similar cluttery was left behind in Ubuntu's file system, not that I can see visibly. I use list-all commands (ls -a), but under the surface I was just curious if more had to be done. Kuddos on the reply. I will try... 

Thanks agian for any advice given...

---

### Post by Elfy on 2014-04-06
You see the period at the front of the name -  .Trash-1000/

Means that it is hidden, in your file manager - Ctrl+H and you will see them.

---

### Post by Jason_Minns on 2014-04-06
Clever keyboard shortcut. I knew how to view hidden files in the terminal, but graphical I did not. Nice.

---

### Post by Impavidus on 2014-04-06
> **Jason_Minns said:**
> sudo rm -rf .Trash-1000/
That's overkill, i.e. a needless risk of collateral damage. **rm -r .Trash-1000/** should suffice on automatically mounted usb drives. Or use the GUI to empty trash. On my system (Xubuntu) it asks whether I want to empty my trash before unmounting the usb drive.

---

### Post by Jason_Minns on 2014-04-06
.Trash-1000/ takes up room on my usb drive. It doesn't seem to harm anything removing it. I will try to use the GUI to empty trash. My system isn't as pollite to ask whether or not I wish to take out the trash. Thanks, I'll keep that in mind.

---

### Post by grumblebum2 on 2014-04-06
If the files on the usb were moved to trash in ubuntu, just emptying trash from the launcher icon 
should also delete that trash from the mounted usb drive.

---

### Post by SeijiSensei on 2014-04-07
Holding down shift while pressing delete removes files completely in most any file manager like Nautilus or Dolphin.  It also works in Windows Explorer.  I was amused that my colleague who is a Windows admin at a client's site didn't know this trick either! 

In Dolphin you can add the Delete command to the right-click context menus as well (Control > Configure Dolphin > Services).

---

### Post by monkeybrain20122 on 2014-04-07
Open Nautilus, from the Files drop down menu (on the top panel) choose Preferences then go to the Behaviour tab, check the box "Include a delete command that bypasses trash", then you will be able to really delete something by right clicking and choose 'delete".

I hate this trash design, it has to be the most useless and stupid feature in all DEs. When I delete something I want it gone, not to be moved to another folder where it quietly sits and takes up space.

---

### Post by 3rdalbum on 2014-04-07
> **Jason_Minns said:**
> My question stems from usb drive transfers between Linux and Windows 8. I started putting a file on a usb drive, and then saw that it was a file that I had already tranfered, so I deleted it off the usb thumb drive. When I opened the thumb drive in Windows 8, I saw that the file, while seemingly was deleted in Linux, showed as a trash file in Windows, and therefore took up space. 

I'm not sure if this is what caused this odd issue, but it might be. On Ubuntu... well, on any operating system except for Windows, you need to unmount a USB drive before removing it. This is because writes to USB devices are cached for speed, and also to avoid prematurely wearing down the flash memory inside a USB stick. If you just ripped the USB drive out of the socket without unmounting it first, there might be data sitting in the cache that has not been written to the drive yet. You would lose that data. Note that the "copy" progress window disappears when all the data has gone into the cache, not when it has actually been written to the disk.

Windows, on the other hand, gets some bytes from the source disk, writes them to the destination disk, then gets more bytes from the source disk, etc. This ends off wearing down flash memory drives quicker and causing lower copy speeds. So why does Windows do it? Because in the days of floppy disks, there was not enough memory for a decent cache, so you could always remove the disk without unmounting it first. As the world transitioned to USB storage devices, people still assumed it was okay to just remove all storage devices without unmounting first. So Microsoft kept this non-caching behaviour as the default in Windows, despite the downsides, because otherwise people would forget to unmount and then would lose data.

Short answer: You need to "Eject" or "Unmount" your USB when you've finished using it on Ubuntu.

---

