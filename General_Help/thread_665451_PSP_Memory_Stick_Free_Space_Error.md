---
title: "PSP Memory Stick Free Space Error"
date: 2008-01-12
forum: General Help
---

### Post by wisemanleo on 2008-01-12
I have about 300mb of free space on my 4gb Sony Memory Stick Pro Duo. Ubuntu thinks there is only about 60mb. I have already tried:

1) Deleting contents of .Trash folder
2) Formatting the memory stick
3) Reinstalling ubuntu

I didn't have this problem when I first started using ubuntu (7.10). I think it started when I decided to try out Rhythmbox to sync files with it. But surely after formatting both the memory stick and ubuntu, that issue would be gone? Unless there's a small-sized file on my psp that has some kind of playlist that its telling Rhythmbox to transfer over everytime it's connected to the computer, hence occupying "allocated" space. That might be possible since I preserved the contents of my PSP before I formatted. But I don't know where or what the file is.

Can anyone help? No other forum topic had a consistent solution.

---

### Post by Hmarroqu on 2008-01-19
Try to reformat it with windows then plop it back into your psp, see the results. Then dont use Rythmbox, or anything else, check it out with nautilus... How do you access it? thru the psp to usb or adapter to PC ?

---

### Post by Arlanthir on 2008-02-07
I have this problem too.
It always happens when I delete/download files with the PSP itself. It's like the free space doesn't update. Windows can read it good, nonetheless :S So what I do is open it on windows, write or delete something there and it's good to go on Ubuntu.

---

### Post by wisemanleo on 2008-02-07
About time someone else has this problem.

I always use a USB cable to connect my PSP to the PC. 
I've formatted the stick and it seemed to finally read properly after. But as soon as I started deleting somethings (and deleting again from .Trash), it failed to read the free space correctly again.

I'm too lazy of a man to try to format every time I want to transfer files to and from the PSP, which I do frequently. For now I'm just booting into Windows when I have to transfer stuff.

*Annoying.*

---

### Post by Arlanthir on 2008-02-07
I've read on other post here that emptying Ubuntu's trash when it does that might help. Worked for another user, so, give it a shot (I will :P)

---

### Post by wisemanleo on 2008-02-07
Hey, thanks for your response, but have you tried *reading* my post? I'll rephrase.

"I've already tried:

1) Deleting contents of .Trash folder
2) Formatting the memory stick
3) Reinstalling ubuntu"

If I went as far as reinstalling ubuntu, I think I would have definitely tried emptying any trash can/box/.hidden folder. In fact, I know I did.

---

### Post by Arlanthir on 2008-02-07
Actually, it's not the folder itself, it's the trash OUTSIDE the device... It's stupidly unrelated, but can't hurt to try... Anyway, just trying to help.

---

### Post by wisemanleo on 2008-02-08
Oh I see what you mean. Excuse me for misunderstanding :(

But I actually did check for that too. Ah well, I guess the only solution is to boot into windows everytime...

It's too bad ubuntu has this retardo .Trash way of doing things. It would be great if it worked just as the same as the way Windows deals with files on flash media.

---

### Post by Arlanthir on 2008-02-08
Yep, just tried it myself and didn't work :(

---

### Post by wisemanleo on 2008-02-08
Yeah, the problem with this is that there's so many factors that could contribute to the error or fixing the error. Is it booting into windows, transferring files, and going back to ubuntu fix it? Is it some random .trash folder? Is it skipping the .trash and just right clicking > delete? What's causing it in the first place? 

Someone somewhere out there should know some sure-fire solution. Or maybe this is a bug?

---

### Post by Arlanthir on 2008-02-08
For me the problem is deleting files in the PSP itself.
Example:
[LIST]
[*]Nautilus says: Free space: 2Gb
[*]Copy a 1Gb file to PSP.
[*]Disconnect.
[*]Delete the file in the PSP menu.
[*](PSP says: free space 2Gb.)
[*]Connect.
[*]Nautlus says: Free space: 1Gb.
[/LIST]

I think it's a bug with ubuntu/gnome/nautilus, because in windows it works OK.

---

### Post by Dedmon on 2008-03-22
I have the exact same issue.  I have a 4Gb Sandisk card in the psp. Itt only started today after I formated the memory stick using the psp. I never formated it since buying the card.

When I delete files using ubuntu the space is shown correctly on both devices. After I deleted 2 files using the psp it shows 956Mb free on it yet ubuntu shows 108.9Mb free when mounted. The difference is exactly the size of the 2 files i deleted using the psp.

Maybe Either the psp doesn't correctly update the file tables properly when deleting or ubuntu doesn't read it correctly.


joe@bloggs:~$ df -h
....
/dev/sdb1             3.8G  3.7G  109M  98% /media/disk

joe@bloggs:~$ fdisk -l
...
Disk /dev/sdb: 4032 MB, 4032823296 bytes
160 heads, 62 sectors/track, 794 cylinders
Units = cylinders of 9920 * 512 = 5079040 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         793     3933169    c  W95 FAT32 (LBA)

---

### Post by Arlanthir on 2008-03-22
It's got to be ubuntu, because it displays correctly in windows too =/

---

### Post by Dedmon on 2008-04-06
The PS3 also seems to have the same issue this can only see the same amount of free space as Ubuntu does even though the PSP says there's more free.

> 
# fdisk -l

Disk /dev/sdc: 4032 MB, 4032823296 bytes
160 heads, 62 sectors/track, 794 cylinders
Units = cylinders of 9920 * 512 = 5079040 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         793     3933169    c  W95 FAT32 (LBA)


# df -h

/dev/sdc1             3.8G  3.1G  740M  81% /media/disk


---

### Post by Dedmon on 2008-04-06
I found the issue :D

It's something to do with LBA (Logical Block Addressing). I luckily fixed the problem using GParted.

In GParted listed under /dev/sdc1 (the psp) it had the flags "boot,lba". I selected "Manage Flags" for that partition and unticked "LBA" and then remounted and refreshed devices and hey presto the correct free space is now showing :D.

---

### Post by Arlanthir on 2008-04-06
Will try when I get the chance :D

EDIT: That didn't work for me :S
Didn't try with reboot though, but... =/

---

### Post by Arlanthir on 2008-04-25
Seems to be fixed in Hardy :D

---

