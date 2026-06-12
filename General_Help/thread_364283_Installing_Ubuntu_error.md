---
title: "Installing Ubuntu error"
date: 2007-02-18
forum: General Help
---

### Post by spartanshalo on 2007-02-18
Hello, I am trying to install ubuntu and have a problem. I burned the ISO image to a Memorex CD-R with Nero and checked that the ISO was burned and not just a file. When I boot from the disk I get to a menu with the Ubuntu title and several options such as start or install, check disk for errors, and so on. If I select to start or install it goes to a black screen and says booting from local disk. It then gives me an error. This is exactly what it says:


*boots to black screen after selecting install

Booting from local disk...

isolinux: Disk error 80, AX=0201, drive 00

Boot failed: press any key to retry...


I do not know what is wrong. Please help, thanks.

---

### Post by taurus on 2007-02-18
How fast did you burn it and by the way, Memorex sucks because I had nothing but trouble using that media?  Switched over to TDK and everything is fine for me since.

---

### Post by spartanshalo on 2007-02-18
I burned it at 48x max speed. I use memorex all the time and never have had a problem. I am trying to install the 6.10 version of the OS also. The computer is a Pentium 3 550mhz processor. I got the i38-sumthin version.

My current worry is due to my download. When I downloaded the ISO it hung at 99% and never finished. It also was no longer responding. The download seemed complete however. I let it sit for a half hour.

---

### Post by taurus on 2007-02-18
Before you burn it, you need to run the checksum to make sure the ISO didn't corrupt.  Then, burn it at a slower speed like 4x.  

Here's a guide that goes through the whole process from downloading to burning.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by spartanshalo on 2007-02-18
Thanks, Ill give it a try.

---

### Post by spartanshalo on 2007-02-18
I just checked the chucksum file and it does not have a thing to compare the 6.10 version too. What do I do?

---

### Post by taurus on 2007-02-18
What was the output of the checksum?

```

283158c7da8c0ada74502794fa8745eb  ubuntu-6.10-alternate-amd64.iso
549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso
5717dd795bfd74edc2e9e81d37394349  ubuntu-6.10-alternate-powerpc.iso
99c3a849f6e9a0d143f057433c7f4d84  ubuntu-6.10-desktop-amd64.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
a3494ff33a3e5db83669df5268850a01  ubuntu-6.10-desktop-powerpc.iso
2f44a48a9f5b4f1dff36b63fc2115f40  ubuntu-6.10-server-amd64.iso
cd6c09ff8f9c72a19d0c3dced4b31b3a  ubuntu-6.10-server-i386.iso
6f165f915c356264ecf56232c2abb7b5  ubuntu-6.10-server-powerpc.iso
4971edddbfc667e0effbc0f6b4f7e7e0  ubuntu-6.10-server-sparc.iso

```

---

### Post by spartanshalo on 2007-02-18
I am downloading Ubuntu again now. Just to be safe if the first download was corrupt. I should also note that when I was navigating the menus at the boot screen for the OS the other options would all become "start or install" if I just cycled through each option.
I will post the result as soon as I can.

It will take about 30-50 minutes to finish downloading and burn the disk.

---

### Post by spartanshalo on 2007-02-18
Oh, by the way, Do you think that Ubuntu is better than Windows 2000 or XP? Maybe even Vista? I have 2000 and access to XP. I have no experience with linux at all.

---

### Post by taurus on 2007-02-18
You probably would have guessed what I would say if you look at the first line of my sig!

---

### Post by spartanshalo on 2007-02-18
OH NOOOOOO!!!! I just noticed that I downloaded version 6.06 instead of 6.10. AHHHHH!
I will just stick with this version then as it has been out longer and therefore must be better off in terms of bug fixes. 

Even now though windows explorer is stuck at 99% complete and says not responing.

---

### Post by taurus on 2007-02-18
Windows explorer is crapped.  If you can't download it using firefox, try using a torrent client since it checks the file while it's downloading.  Then, you probably don't need to run the checksum before you burn it at 4x speed.

---

### Post by spartanshalo on 2007-02-18
Finally it completed. Now attempting to use the checksum thingy.

---

### Post by spartanshalo on 2007-02-18
Is this the correct check thing for version 6.06? fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso

---

### Post by taurus on 2007-02-18
> **spartanshalo said:**
> Is this the correct check thing for version 6.06? fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso

```

b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
**fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso**
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso

```
Looks good to me.  Now, burn it at 4x.

---

### Post by spartanshalo on 2007-02-18
Thanks for your help so far. After I burn it I just boot it up in the old pc correct? Then install my replacement for windows? ;)

---

### Post by taurus on 2007-02-18
Yip.  Make sure you set your BIOS to boot from the CD-ROM first.  Then, click the install icon on the desktop and tell it to use the whole harddrive, erasing Windows from it.

---

### Post by spartanshalo on 2007-02-18
The PC I am putting it on first has no OS on it. Will it boot up correctly? I have intalled fresh copies of wn2k and xp before.

---

### Post by spartanshalo on 2007-02-18
well it looks like it is booting up fine so far. I will stick with 6.06 for a while. what is different in 6.10? THanks for the help.

---

