---
title: "can't access files on dvd"
date: 2008-06-24
forum: General Help
---

### Post by kombipom on 2008-06-24
Hi,

I've upgraded to hardy (dist-upgrade from gutsy) and my DVD drive is acting weird.  When I insert a disk it mounts OK and I can see the files on it but I can't access any of them. They are avi files and I can play avi files I have on my hard disk.  I've tried watching the files in Totem, mplayer and vlc with no luck.  totem just freezes up and mplayer and vlc complain about not being able to "seek". It also won't play any DVD movie disks and I have the medibuntu stuff installed.

Any ideas?

---

### Post by danwood76 on 2008-06-24
It sounds like a faulty DVD drive.

Run the media check from the live CD, this will also test the drive to an extent though it wont test the DVD laser only the CD laser within the drive.

Does this only happens with DVDs?
In other words can you mount CD's?

---

### Post by WRDN on 2008-06-24
In the terminal, run the command:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

I had to run this before I could play DVD's.

---

### Post by danwood76 on 2008-06-24
Yes but he is having issues playing avi's from a DVD, this doesnt need the dvd decryption stuff to play.

---

### Post by kombipom on 2008-06-24
I can play audio CDs OK I just can't open any files from DVDs.

---

### Post by danwood76 on 2008-06-24
It sounds like the DVD laser diode has died (is dying) in your drive.
You see a combi CD/DVD drive has 2 laser diodes one for each type, its common for one to die and the other to still be working, this used to happen commonly of the PS2 ;)

If you can get hold of another DVD drive it might be worth testing in the system just incase its some other fault before replacing the drive.

---

### Post by danwood76 on 2008-06-24
Just had a thought it might be worth checking the end of dmesg to see if there are any kernel errors after it mounts the DVD.

So stick a DVD in let it automount then open up the terminal and paste the following command:
```

dmesg | tail

```
and post the results here

---

### Post by kombipom on 2008-06-25
dmesg output:

[  154.219779] Buffer I/O error on device sr0, logical block 15
[  154.219781] Buffer I/O error on device sr0, logical block 16
[  154.219784] Buffer I/O error on device sr0, logical block 17
[  154.219786] Buffer I/O error on device sr0, logical block 18
[  154.219789] Buffer I/O error on device sr0, logical block 19
[  154.219791] Buffer I/O error on device sr0, logical block 20
[  154.219793] Buffer I/O error on device sr0, logical block 21
[  154.348926] UDF-fs: No VRS found
[  154.372401] ISO 9660 Extensions: Microsoft Joliet Level 3
[  154.405232] ISOFS: changing to secondary root

It seems I need VRS (whatever that is).  Google here I come...

---

### Post by kombipom on 2008-06-25
OK, after a bit of googling about VRS I found out that it's not something I need to add support for.  I looked a bit further back in dmesg and it seems I have hardware problems.  Out with the screwdriver and a spare cable & old drive.

Thanks for the help guys, I should have known to dmesg.

---

