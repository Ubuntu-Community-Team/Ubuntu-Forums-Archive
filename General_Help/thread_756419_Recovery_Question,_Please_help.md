---
title: "Recovery Question, Please help"
date: 2008-04-15
forum: General Help
---

### Post by penguin5 on 2008-04-15
While installing ubuntu 7.10, I deleted the D drive on my acer laptop. Because of that, i was not able to make a factory default CD because the image was on the D drive. But Acer does have a hidden partition. Im not sure what its for. 

My question is this, today I actually restored my vista to factory settings through the dual boot menu . It did not mess with Ubuntu Partition but it did not recreate the D drive with the recovery image. I cant make a recovery CD through vista because it says that there is not enough space on the D drive.  So if I was able to recover my system, how can I make a CD so I can do the same on my other HDD? Might the hidden partition be the recovery partition just like the D drive was? Should I somehow recreate the D drive so I can make  the backup CD?If at all possible. 

Thank you.

---

### Post by Diabolis on 2008-04-15
Use gparted, which comes in the live-cd. Use it to restore your hard drive, set it as it came when you bought your pc. Probably after that you can make your back up cd.

---

### Post by penguin5 on 2008-04-15
I would love to restore my laptop to factory default. But How do I recreate the D drive and also make it so it is recognized by Acer as the default D drive. I thought that gparted only partitioned drives not set them as C or D or E etc.

---

### Post by Diabolis on 2008-04-15
erase all your partitions, except the "hidden one". It contains the recovery files, then make a new partition using all the free space and set the file system to ntfs. Thats is the closest you can get to factory defaults. The C, D... labels are set by windows, so I don't know if you can set them manually.

Reboot, and in the grub menu you should see an entry with the title windows. It should correspond to the "hidden partition", boot from it and it will guide you through recovery mode.

---

### Post by penguin5 on 2008-04-15
I have the hidden partition, Vista partition C Drive, Swap Linux and Ubuntu. So I need to delete all of it and combine them into one C Drive and then reinstall Vista that way? Does leaving ubuntu partition alone and just erasing the vista one and setting it to ntfs work? 

Sorry for asking stupid questions, your help is appreciated.

---

### Post by Diabolis on 2008-04-15
> Does leaving ubuntu partition alone and just erasing the vista one and setting it to ntfs work

It should work, I have done it that way with a windows xp computer.

> I cant make a recovery CD through vista because it says that there is not enough space on the D drive.

I though that you didn't care about the ubuntu installation, since you probably have a live cd, you can reinstall it anytime. But if you do, then you have to shorten your ubuntu partition, just while you make you windows back up. gparted can do this without wrecking the ubuntu installation.

I don't know how much space you need for vista, but for xp the minimum was 4gb, I think. Just make a partition big enough for vista.

---

### Post by penguin5 on 2008-04-15
I did what you said and I still got vista with only a C drive. Should I have made two equal partitions so vista recovery could make C and D by itself? I tried to make a system backup onto my CD and it said the same thing "not enough memory on D drive" 

Any suggestions?

Thank You

---

### Post by Diabolis on 2008-04-15
> I still got vista with only a C drive

If your hard drive is C, probably your cd-rw unit is D.

> "not enough memory on D drive"

If what I said is true, then the back up is to big to be stored in a cd, thats why you get an error. You have to use a dvd or burn it into multiple cds.

---

### Post by penguin5 on 2008-04-15
I cant burn it on multiple CDs because it will not even let me start burning it on the first one. As soon as I put a blank CD-R and try to burn, it gives me that message. I dont have a DVD burner. 

All Im trying to do is to get vista on my new HDD so I can partition it and get ubuntu on it. So thats why I need to get a copy of the recovery CD. Buying it from Acer is $30.  The harddrive I have right now is too small so I want to get vista on my new 120GB. 

Thanks again for your patience

---

### Post by Diabolis on 2008-04-15
I'm not sure if thats possible, I have never done it. However, the objective of the thread is to burn the back up. 

What you can do is make a virtual dvd-rw unit. Then make the back up, and "burn it" through the virtual dvd. See if you can save it as a .iso file.

 then try to install vista with the newly created .iso file, this files can be mounted as if you actually had inserted a cd.

I haven't used windows vista, so I can't recommend you any software for this task, sorry.

You will probably have sucess at making the back up, but I'm not sure about installing it into another hard drive.

---

### Post by penguin5 on 2008-04-16
Im going to try something drastic. Ill let you know how it goes. Thanks for everything.

---

### Post by penguin5 on 2008-04-16
I uninstalled Ubuntu and Vista and combined the partitions together. And I also kept the hidden vista partition. But then when I rebooted, it gave me a GRUB error and not the "menu" that I expected. So i had no way of choosing to install from the hidden partition. Then I reinstalled ubuntu instead and got to the menu and selected windows, but it gave me a recovery error. 

I feel like  if I dont get the image on my CD from the hidden partition and make it work, Ill just give up because the only reason I want vista on my laptop is for "what if" situations. 

Are there any programs for ubuntu that make hidden partitions available to mess around with?

---

### Post by Diabolis on 2008-04-16
> I uninstalled Ubuntu and Vista and combined the partitions together. 

If you do that you won't have a boot-able partition, that is why you got the grub error. Do it from a live-cd and instead of deleting both partitions, just resize the windows disk. Resize it so it occupies your full disk, except the recovery partition.

---

### Post by penguin5 on 2008-04-16
But now all I have is ubuntu  partition with the swap space and the hidden vista partition.Isthere a way to boot from the vista hidden partition?

 I tried to select the windows option from the menu but i gave me an recovery error. I think it might be because I have the entire space occupied with ubuntu .

Thanks

---

### Post by Diabolis on 2008-04-16
Yes, you are right. Shrink ubuntu and make a partition big enough for vista.

---

### Post by penguin5 on 2008-04-17
I just installed ubuntu on a 13GB partition so I could access the menu and select the recovery for vista. It let me recover but when it says that recovery is complete and lets me to restart, but when I do the vista does not even show up, just the recover and Ubuntu options again. 

I gave it plenty of space and the gparted shows that it has been installed but I cant get into it. Does it have to do with being mounted? All my partitions are highlighted with a light blue outline in gparted and there is a set of keys picture right next to it. Any ideas?

---

### Post by Diabolis on 2008-04-17
Everything is correct. The problem is that grub can't see vista because it was installed after grub.

Reinstalling grub should fix it, is quite simple.

while at grub menu press c then follow this:

```

find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

---

### Post by penguin5 on 2008-04-17
> **Diabolis said:**
> Everything is correct. The problem is that grub can't see vista because it was installed after grub.

Reinstalling grub should fix it, is quite simple.

while at grub menu press c then follow this:

```

find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

When I type find /boot/grub/stage 1  it shows this (hd0,6)
Then Im not sure what to put in for ? It gives me an error. How do I know what to type in? I tried typing in root /(hd0,6) but no good.

---

### Post by Diabolis on 2008-04-17
root /(hd0,6) wrong

root (hd0,6) correct, note the space between root and the first parenthesis.

the next command will be:

setup (hd0)

---

### Post by penguin5 on 2008-04-17
I tried it and it did not give me the errors and it accomplished the process successfully . Unfortunately, I still cant get to load vista. I appreciate you trying to help me.  Im not sure what to do. I guess Ill try to focus on burning that partition onto a CD some other way.

---

### Post by Diabolis on 2008-04-17
Grub was supposed to add the windows entry to its menu after that, since it didn't you have to add it manually. You just have to edit your menu.lst file and add a chainloader.

first
```
sudo gedit /boot/grub/menu.lst
```

then add to the end of the file this:
```
title  Microsoft Windows Vista
root   (hd?,?)                     #Vistas partition number
savedefault
makeactive
chainloader +1
```

---

### Post by penguin5 on 2008-04-17
hate to double post but I found the Recovery Acer drive. Its about 4.5GB and I wish to burn it on CD's. Do you think that would make the boot CDs?

---

### Post by Diabolis on 2008-04-17
Lets suppose that you burn the whole recovery partition to a dvd. As I said I'm not sure if you can use that copy to recover your whole system in the future. I have never tried it, maybe I'll give it a shot in a month or whenever I  have time.

So I focused on helping you boot into vista and burning your recovery cd.

You can try this: boot into vista and make the recovery cd. Burn it as a dvd, in multiple cds or save it as a .iso. Then remove your hard drive, plug in your other drive and try to "recover" your system.

---

### Post by penguin5 on 2008-04-17
> **Diabolis said:**
> Grub was supposed to add the windows entry to its menu after that, since it didn't you have to add it manually. You just have to edit your menu.lst file and add a chainloader.

first
```
sudo gedit /boot/grub/menu.lst
```

then add to the end of the file this:
```
title  Microsoft Windows Vista
root   (hd?,?)                     #Vistas partition number
savedefault
makeactive
chainloader +1
```

this is what i typed in: title           Microsoft Windows Vista
root            (hd0,6)                     
savedefault
makeactive
chainloader +1

It lets me choose Vista but fails to load it.

---

### Post by Diabolis on 2008-04-17
the line that says "root" will tell grub where vista is installed, so is not possible that vista is installed in hd0,6. I already saw that ubuntu is installed in this partition, I know that because that is from where you reinstalled grub in the other post.

If you only have one disk plugged in then your vista installation must me something like **(hd0,?)**

You can see the numbers os your partitions with this command:
```
sudo fdisk -ul
```

---

### Post by penguin5 on 2008-04-17
here is what i get:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    17735759     8867848+  12  Compaq diagnostics
/dev/sda3        17735760   156296384    69280312+   5  Extended
/dev/sda5        17735823    85401539    33832858+   7  HPFS/NTFS
/dev/sda6       150561243   156296384     2867571   82  Linux swap / Solaris
/dev/sda7       123459588   150561179    13550796   83  Linux
/dev/sda8        85401603   123459524    19028961    b  W95 FAT32

Im not sure what number to use. hd0,5?

---

### Post by Diabolis on 2008-04-17
probably this one is vista

/dev/sda5 17735823 85401539 33832858+ 7 HPFS/NTFS

and this one is the recovey partition

/dev/sda8 85401603 123459524 19028961 b W95 FAT32


This is strange, you used (hd0,6) before which would indicate that you have 7 partitions, but you only have 6.

A good guess would be to try (hd0,0), if it doesn't work it won't hurt. You can keep guessing numbers until you get it right.

Or you can open gparted and see all your partitions, ignore the "sda" numbers and focus on the order in which the partitions appear. The first one from left to right is (hd0,0) the second one is (hd0,1) and so on.
Through this method you can see which is the partition number of your vista installation.

Sorry about the fdisk command, I though that it would give us the hd number.

---

### Post by penguin5 on 2008-04-17
First of all, I would like to thank you for all of your help. Everything WORKED!!! I installed my new HDD and used the recovery folder which I saved my my 8GB mp3 player and then installed ubuntu and installed vista from the recovery folder. Now I have my 120GB HDD with vista and ubuntu. Now All I have to do is to tweak a few things but other than that Im happy with what I have now. Hope I dont jinx everything. 

Thanks again for all of your help!

---

### Post by Diabolis on 2008-04-17
I'm glad you got everything working and is good to know that you can use recovery partitions like that.

---

