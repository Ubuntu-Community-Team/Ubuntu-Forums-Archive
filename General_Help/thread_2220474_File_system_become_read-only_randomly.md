---
title: "File system become read-only randomly"
date: 2014-04-28
forum: General Help
---

### Post by bruttezze on 2014-04-28
[COLOR=#000000][FONT=Droid Sans]Hi!
From yesterday randomly the filesystem of my Ubuntu 13.10 installation becomes read-only until a new reboot. I want to fix that... I really need your help, but I can give some informations (perhaps useful):
1)I recently changed size at the partition, creating another one with 50 GB of the primary. I did that with gparted on live usb Trisquel
2)I recently changed /etc/fstab adding the line
"UUID=454E045C147EC335 /media/MoYan ntfs auto,rw,exec,users,dmask=000,fmask=111,nls=utf8 0 0"
for automatically mount the partition created in 1)
3)When I switch on it ask me something like that: "There is an error: F for trying to fix it, I to ignore, E to not mount, M to manual solution to the problem". I tried F and I, without any success...[/FONT][/COLOR]
[COLOR=#000000][FONT=Droid Sans]Please reply, cause I really don't know what to do and I don't want to format another time the partition... =([/FONT][/COLOR]
[COLOR=#000000][FONT=Droid Sans]Thank you all![/FONT][/COLOR]

---

### Post by Impavidus on 2014-04-28
When a file system suddenly becomes read-only it usually encountered an I/O error. That is, you may have a bad hard drive. Try to check your drive's smart status.

---

### Post by Bashing-om on 2014-04-28
bruttezze; Hi !


This;
> 
/media/MoYan ntfs 

Indicates NTFS format to that partition. NTFS being a Windows format, use Windows' tools to check that file system and repair it .

[INDENT][INDENT]hey,
[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bruttezze on 2014-04-28
Impavidus: How can I do that?
Bashing-Om: It is not the ntfs filesystem that becomes read-only, is the Ubuntu partition which do that stuff...

---

### Post by bruttezze on 2014-04-30
Up

---

### Post by Impavidus on 2014-04-30
Not sure which tools are installed by default. You may have the disk utility.

What certainly works is smartctl. Run```
sudo smartctl -a /dev/sda
```If it complains that the program hasn't been installed, first install it using```
sudo apt-get install smartmontools
```. If you get errors while installing, try it from a live disk.

---

### Post by bruttezze on 2014-04-30
[http://pastebin.com/vpPQjGTr](http://pastebin.com/vpPQjGTr)
This is what the terminal said.. Does that tell us anything?

---

### Post by Impavidus on 2014-04-30
That seems OK. Your drive still looks healthy. I'm open for other suggestions.

Edit: that is, /dev/sda looks OK. I assume that's your drive, but if you have multiple drives it may be called differently (like /dev/sdb). Bashing-om's post below will tell.

---

### Post by Bashing-om on 2014-04-30
bruttezze; Welp;

Maybe it is time to have a definition of the devices we are looking at, and know where to point the file system checkers to.
Post back the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```

[INDENT][INDENT]file system checks are
[INDENT][INDENT][INDENT]cheap insurance
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bruttezze on 2014-04-30
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Identificativo disco: 0x69b53599

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   574216191   287107072   83  Linux
/dev/sda2       679688192   683882495     2097152   82  Linux swap / Solaris
/dev/sda3   *   683887050   976768064   146440507+   7  HPFS/NTFS/exFAT
Partition 3 does not start on physical sector boundary.
/dev/sda4       574216192   679688191    52736000    7  HPFS/NTFS/exFAT

Le voci nella tabella delle partizioni non sono nello stesso ordine del disco
```
First output
```
Modello: ATA TOSHIBA MQ01ABD0 (scsi)
Disco /dev/sda: 500GB
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: msdos

Numero  Inizio  Fine   Dimensione  Tipo     File system     Flag
 1      1049kB  294GB  294GB       primary  ext4
 4      294GB   348GB  54,0GB      primary  ntfs
 2      348GB   350GB  2147MB      primary  linux-swap(v1)
 3      350GB   500GB  150GB       primary  ntfs            avvio


Avviso: Impossibile aprire /dev/sr0 in lettura-scrittura (File system in sola
lettura). /dev/sr0 è stato aperto in sola lettura.
Errore: /dev/sr0: etichetta del disco non riconosciuta
```
Second output
```
matsetes@matsetes-X55C:~$ sudo parted /dev/sda unit s print
Modello: ATA TOSHIBA MQ01ABD0 (scsi)
Disco /dev/sda: 976773168s
Dimensione del settore (logica/fisica): 512B/4096B
Tabella delle partizioni: msdos

Numero  Inizio      Fine        Dimensione  Tipo     File system     Flag
 1      2048s       574216191s  574214144s  primary  ext4
 4      574216192s  679688191s  105472000s  primary  ntfs
 2      679688192s  683882495s  4194304s    primary  linux-swap(v1)
 3      683887050s  976768064s  292881015s  primary  ntfs            avvio

```

---

### Post by Bashing-om on 2014-04-30
bruttezze; OK,

Let's run a file system check on the ubuntu partition.
#From liveDVD as the partition MUST be unmounted, -  swap off if necessary, (with GParted)-.
#e2fsck is used to check the ext2/ext3/ext4 (the 83 says this is ext4) family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck for full disclosure.
```

sudo e2fsck -f -y -v /dev/sda1

```

Reboot into the installed system and let's see if the partition now behaves it's self.

[INDENT][INDENT]nothing more than a thing ?
[/INDENT][/INDENT]

---

### Post by bruttezze on 2014-04-30
I think that in the second it's sda1 and not sdb1... Cause sdb1 is the live filesystem
Have I to post the results? Can this solve the problem? I have not understood well that...
I ran both them

---

### Post by Bashing-om on 2014-04-30
bruttezze; Yike !

You are correct 'sda1" I stand corrected and will correct my posting.

As Yes I do expect the file system check/repair to fix your problem.

Have you rebooted to this time, all is good now ?

[INDENT][INDENT]to err is human but as it happens to often,
[INDENT][INDENT][INDENT]what am I [/INDENT][/INDENT][/INDENT] [/INDENT][/INDENT]

---

### Post by bruttezze on 2014-04-30
I tryed just now, but, after almost 20 minutes, it became read-only, as usual. This time didn't appear the message during the switch on.

---

### Post by Bashing-om on 2014-04-30
bruttezze; Sorry,

That was my only shot. Now I too am open to others suggestions.
Maybe reading the log files will prove productive (??).

[INDENT][INDENT]there has got to be a reason
[/INDENT][/INDENT]

---

### Post by bruttezze on 2014-05-01
Well, where can I find the log?

---

### Post by SeijiSensei on 2014-05-01
If you ran e2fsck from the installation CD/DVD and corrected any errors, but the filesystem became read-only after use, I'm going to guess it's a hardware problem with the drive itself. 

Use "sudo more /var/log/syslog" to see if the OS reports problems with the drive.  There are ways to fix a system with some bad sectors, but you'd have to reformat the drive, reinstall Ubuntu, and restore any other data from backups.

You can also install the **smartmontools** package and use it to analyze the drive.  Read [this document](https://help.ubuntu.com/community/Smartmontools) for details.

---

### Post by Impavidus on 2014-05-01
Apart from a bad drive it could also be a loose cable. Try unplugging the hard drive and plugging it back in.

---

### Post by bruttezze on 2014-05-11
Seiji Sensei: this is the output of sudo more /var/log/syslog
[http://pastebin.com/FfmwHFu5](http://pastebin.com/FfmwHFu5)

---

