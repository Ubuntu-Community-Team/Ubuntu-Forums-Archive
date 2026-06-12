---
title: "Ubuntu dual boot with Vista"
date: 2007-10-28
forum: General Help
---

### Post by Innovavious on 2007-10-28
Well, today i thought id give Ubuntu a try for a while so i cleared out one of my partitions which was just filled with crap and installed it. Now Ubuntu is working perfectly with no problems (well, expect for i downloaded the i386 version accidentally and the fact that websites take ages to load but downloads go at full speed but they arnt really a problem right now) but i cant get back to vista. I assumed that grub would of automatically detected vista or something like that but it seems i assumed wrong. Ive tried adding it myself but to no avail. 

I added this to the grub file

```
title 		Vista
root		(hd0,0)
savedefault
makeactive
chainloader +1
```

I also tried (hd0,1), (hd0,2) etc. Whenever i try it i get 

Error 12: invalid device requested

I also got the output from fdisk -l here if thats useful

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6eab6ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15356928   83  Linux
/dev/sda2            1913       19456   140922180    f  W95 Ext'd (LBA)
/dev/sda5            1913       10836    71681998+   7  HPFS/NTFS
/dev/sda6           10837       15416    36788818+   7  HPFS/NTFS
/dev/sda7           15417       19456    32450560    7  HPFS/NTFS
```

Vista should be on sda7.

I know vista is still there, i named the partition it is on "Windows" and it shows up in Ubuntu with all the files still there. Re-installing vista is a last resort right now. Vista is very temperamental with me and activations. If i re-install it is going to want to be activated again and each time ive had to do that so far its failed and ive had to phone up Microsoft to get a new activation code.

Anywho, any idea what i can do?

---

### Post by Jose Catre-Vandis on 2007-10-28
If Vista is on sda7 then your menu.lst should read:
```
title 		Vista
root		(hd0,6)
savedefault
makeactive
chainloader +1
```

I am assuming sda5 and sda6 are "hidden" directories for restore etc?

---

### Post by Innovavious on 2007-10-28
> **Jose Catre-Vandis said:**
> If Vista is on sda7 then your menu.lst should read:
```
title 		Vista
root		(hd0,6)
savedefault
makeactive
chainloader +1
```

I am assuming sda5 and sda6 are "hidden" directories for restore etc?

sda5 has all my large windows applications on it and sda6 is files and smaller apps.

I didnt make any of these partitions for ubuntu, i made these all when i got vista ages ago. The one ubuntu is on was origanally gonna be for windows xp in case i had any major problems with vista but i didnt so it just ended up as a random file dump. The only thing i changed when i installed ubuntu was the file system on the partition i was installing to.

Anywho, i tried 0,6 and that didnt work

---

### Post by meierfra on 2007-10-28
Vista need to be on a primary partition to boot. (Unless you have  another primary Windows partition. Which I assume you used to have, but  deleted to  installed Ubuntu) 
You might be able to use  the GParted Live CD to move Vista to primary partition. 
Also  the following thread might help [http://ubuntuforums.org/showthread.php?t=552832]("http://ubuntuforums.org/showthread.php?t=552832")

I'm not sure whether any of that will work. If all fails back-up your files  and reinstalled Vista on a primary partition.

---

### Post by Jose Catre-Vandis on 2007-10-28
Oh, and if you moved Vista (e.g. with Gparted) to make way for Ubuntu you might have real problems. It doesn't like being moved or resized by 3rd party programs! :!

---

### Post by Innovavious on 2007-10-28
Wow, no wonder i couldnt log in, ill spelled my username wrong when i signed up, supposed to be innovacious....

Anywho, as i said above, the only thing i changed when i installed ubuntu was the file system on the partition i was installing too. Ive tried loads of different combinations of stuff in the grub file now and messed around with supergrub for a bit but i got nothing. If i format the partition with ubuntu on would my computer revert back to booting windows?

---

### Post by Innovavious on 2007-10-28
well, it looks like i am going to have to re-install vista. i just put in the dvd to see if i could boot from that somehow and apparently vista isnt installed. Even though all the files are still there and the ubuntu installation SHOULDNT of touched the partition its on... 

Now im gonna have to phone microsoft again to get another new activation code off of someone i can barley understand :( i wish i didnt have to use windows but its the only option for so many things :(

---

### Post by meierfra on 2007-10-28
>  ubuntu installation SHOULDNT of touched the partition its on..

Ubuntu did not touch the vistas partiton. The problem is that  Vistas had  it boot up information on a different partition.

---

### Post by Gas_Man on 2007-10-28
change your grub to sda0,6 and ut will work after you run ```
Sudo grub-install /dev/sda
```

---

### Post by Gas_Man on 2007-10-28
ops! disregard this part
> **Gas_Man said:**
> change your grub to sda0,6 

leave the grub menu at hd0,6 and then run ```
sudo grub-install /dev/sda
```

and if that doesn't work change it to sd0,6 and then run the grub-install /dev/sda 

you should get a confirmation message similar to this:
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda
(hd1)   /dev/hdc

i'm using ide hdd's and not sata or usb hdd's ...
good luck

---

