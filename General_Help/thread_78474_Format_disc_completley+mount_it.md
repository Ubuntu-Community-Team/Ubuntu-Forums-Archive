---
title: "Format disc completley+mount it?"
date: 2005-10-18
forum: General Help
---

### Post by UbuntuUbuntu7 on 2005-10-18
I was about to format my former Win2000 entire ntfs disc to ext3 and use it as a download media.... well, so i thought. Because it seems harder then i thought. How do i do? And is this future mount line(hdb1) the correct one?: Im here thinking specially about the last numbers who to me seems completley random...

proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
***_/dev/hdb1 /media/disk ext3 defaults 0 0_***

eek: :cool:

---

### Post by Murgle on 2005-10-18
you are unsure about the 0 0 at the end? that should be fine just the way it is.  I don't see anything wrong with that.  I believe that to let anyone write to the drive you should add user or utf=000 (I think anyway it should be in the man page) after defaults on that line.  If that isn't there then only whoever mounted it can write I think

---

### Post by UbuntuUbuntu7 on 2005-10-18
Ok, i did this: *sudo mkfs.ext3 /dev/hdb* then i guess the drive is formated and ready i hope.

Then i did this: **sudo mount /dev/hdb1 /media/disk ext3 defaults,utf=000 0 0** (It didn t work)
and this: **sudo mount /dev/hdb1 /media/disk ext3 defaults,user 0 0** (It didnt work), in both instances i get this messages, which talks about mounting: 

[I]Användning: mount -V                  : visa version
            mount -h                  : visa denna hjälptext
            mount                     : visa monterade filsystem
            mount -l                  : samma, inklusive volymetiketter
Det var den informativa delen. Nu kommer vi till montering.
Kommandot är "mount [-t filsystemstyp] någonting här".
Detaljer som kan hittas i /etc/fstab kan utelämnas.
            mount -a [-t|-O] ...      : montera allt i /etc/fstab
            mount enhet               : montera enhet på den kända platsen
            mount katalog             : montera känd enhet här
            mount -t typ enhet kat    : vanligt monteringskommando
Observera att man egentligen inte monterar en enhet, utan ett
filsystem (av angiven typ) som finns på enheten.
Man kan också montera ett redan synligt katalogträd någon annanstans:
       mount --bind gammalkatalog nykatalog
eller flytta ett underträd:
       mount --move gammalkatalog nykatalog
En enhet kan anges med namn, exempelvis /dev/hda1 eller /dev/cdrom,
eller med etikett, genom att använda  -L etikett  eller med uuid,
genom att använda  -U uuid.
Andra flaggor: [-nfFrsvw] [-o flaggor] [-p lösenordfd].
Säg  man 8 mount  för många fler detaljer.[/I]

What to do?

---

### Post by Murgle on 2005-10-18
did you write those lines at the command prompt or did you store them in your /etc/fstab file?  they should be stored in the file and at the prompt after you put that in your fstab with out the sudo part, type mount /media/disk and you should be good.

---

### Post by UbuntuUbuntu7 on 2005-10-18
[QUOTE=Murgle]did you write those lines at the command prompt or did you store them in your /etc/fstab file?  they should be stored in the file and at the prompt after you put that in your fstab with out the sudo part, type mount /media/disk and you should be good.[/QUOTE]

Yes i have put it in the fstab. Then wrote in the terminal: 

sudo mount /dev/hdb1 /media/disk

The answer is something like this: *"mount: you have to specify the filesystem type."*

---

### Post by Murgle on 2005-10-18
ok then you need to type

sudo mount /dev/hda1 /mountpoint -t ext3 or whatever it is.

---

### Post by UbuntuUbuntu7 on 2005-10-18
[QUOTE=Murgle]ok then you need to type

sudo mount /dev/hda1 /mountpoint -t ext3 or whatever it is.[/QUOTE]

Ok, did this:  sudo mount /dev/hdb1 /media/disk -t ext3

And gets this: special unit /dev/hdb1 doesn exit.

But listen here. If i mount with: sudo mount /dev/hdb /media/disk (yeah, thats without the number one), then it gets mounted, even though the number one is in the fstab. But there is a folder in the disk that says "lost+found" that i cant access. 

If i mount with sudo /dev/hdb /media/disk again, and change so there is no number one in fstab, the exact same thing happens. :rolleyes:

Do i have to make a partition or something?

---

### Post by Murgle on 2005-10-18
if you could type sudo cfdisk /dev/hdb and tell us what you see, it should list off all the partitions on hdb.  Then we can hopefully get to the root of the problem

---

### Post by UbuntuUbuntu7 on 2005-10-19
Actually it&#347; fixed now. I did a new partition on the disk and formated it. 
But i dont think it did any difference, because, i still had "lost+found" folder in the disk, and i couldnt write to it... the problem was, though that the permissions on the drive wasnt right, so i changed it with a command i found here on the forum. Thanks for your will to help. :D

---

