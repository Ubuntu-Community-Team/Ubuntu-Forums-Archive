---
title: "Ubuntu install failure :("
date: 2008-06-18
forum: General Help
---

### Post by mbw163 on 2008-06-18
hello everyone,
I recently tried to install ubuntu on my sony vaio sz laptop. I already had vista and xp on it. well i booted into the ubuntu installer and got as far as the partition manager (both times i tried to install it)

The first time I could not use the space i took from vista to create the second partition (ext3). originally i took 50gb of free space from vista and took 1gb for swap. then the rest of the space left over was listed as unusable. Well I tried the ext3 first and i could not get the swap partition then. so i decided to have vista take back that unused space and call it quits for the first night.

Night 2:
I decided to install it again. Got to the same part. this time instead of first taking 50gb away i chose 1000mb swap file. Well i got some sort of error with failure and abort partition in it. so i did and then all of a sudden my whole vista partition becomes swap! 

Then i put in my vista disk, and vista couldnt find the vista drive.
Went into ubuntu to change swap partition back into ntfs.
rebooted and partition said that bootmgr is missing (press ctrl+alt+delete)

So is there a chance of getting vista back? It still shows the 22gb of space used up (when I had vista)
my xp drive is still showing in the live cd, but i cant boot to it since vista was the boot manager.

Please help!
BTW (this was posted over at Notebook review forums as well)

---

### Post by VMC on 2008-06-18
There's a program called [EasyBCD]("http://neosmart.net/dl.php?id=1") that should be able to recover your Vista again.
If you have a Vista cd insert that and select repair option. If you don't, your in luck. The same people that brought EasyBCD bring [URL="http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"]Vista recover CD
[/URL]
After everything is back to normal try to let ubuntu use free space and it will default to correct file system and swap.

---

### Post by mbw163 on 2008-06-18
i have the vista disk, but when i put that in and do a system recovery, it doesnt work. 
 (the operating system does not show up when I need to select the drive vista is in)

the vista recov cd is just the vista program dvd right?

---

### Post by mbw163 on 2008-06-18
I'll try to explain it in more detail, but I dont know if I can.

I got to the partition part of the installation of Ubuntu and I went into the vista partition to edit it. I selected 1000mb and chose that as my swap. 

The warning came up saying this change is permanent with the go back or continue button. I continued on.

Then before the formating or whatever could finish, an error came up saying that the partition failed and that it would need to abort. SO the only choice was to accept it. Then my vista partition automatically became a 90GB partition worth of SWAP. (i dont know how this happened.)

I tried to undo it (with the button on the left hand side) but that was no use. SO i decided to exit out of installer. Went to reboot my computer and it said (No operating system or missing operatign system)
So I put in the vista disk to try to repair the thing, but the partition for vista does not show up when i get to this [IMG]http://i.i.com.com/cnwk.1d/i/tr/Eve/figs02142008vista/H.png[/IMG]

So i went back into ubuntu to look for my drives. Didnt find it in the my computer so i opened up gparted.  I switched the swap partiton back into NTFS, since I thought that would help somehow. It still showed the disk space used (about 22gb which I believe was the vista files etc.)

Now since its in NTFS, I rebooted and the error this time says that a bootmgr is missing. 


So my question is.... is there a chance of getting vista back? Without having to reinstall vista from the dvd disks?
my xp drive is still showing in the live cd of ubuntu, but i cant boot to it since vista was the boot manager.

I dont know if this clears it up a bit....

---

### Post by mbw163 on 2008-06-18
double post

---

### Post by mbw163 on 2008-06-19
had to reinstall vista and xp.

this time got it to work because I only gave vista 40gb and the rest was just left alone.

---

