---
title: "[SOLVED] Packet Writing without Tears???"
date: 2006-09-10
forum: General Help
---

### Post by Cariboo1938 on 2006-09-10
Hello all,
I'm stuck on "packet writing" despite great help from 'dradul', to whom I give thanks -- here-- again! 
(see: [Here]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+Writing+tears"))
I started this thread new and I hope the administrators will forgive me!
I'm so close but I just don't know enough about Linux/Ubuntu to get it done. 
Maybe there is somebody who has mercy on me and helps me to forget my 'tears'?
Here is my last post in [COLOR="DarkOrange"]HOW-TO: Packet Writing without tears[/COLOR]:
> [QUOTE]:
Originally Posted by dradul: [View Post:]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+Writing+tears")
You may need to disable the other, default, entries. The message means that the cd has already been mounted as a read-only volume probably. You can solv it by setting the default entries to be "noauto" and using pmount to mount them as neded.

[COLOR="Blue"]Where can/must I do this "disable the other, default, entries"?
Would it be in /etc/fstab?[/COLOR]

I have tried [COLOR="Red"]this[/COLOR], altough the default entries alreadly were 'noauto':
> 
# /etc/fstab: static file system information.
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0

/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda3 /Storage ext3 defaults 0 2
/dev/sda1 /boot ext3 defaults 0 2
/dev/sda5 /home ext3 defaults 0 2
/dev/sda6 /usr ext3 defaults 0 2
/dev/sda7 /var ext3 defaults 0 2
/dev/sda8 none swap sw 0 0

[COLOR="Red"]#[/COLOR]/dev/hda /dev/dvdrw udf,iso9660 user,noauto 0 0
[COLOR="Red"]#[/COLOR]/dev/hdb /dev/cdrw udf,iso9660 user,noauto 0 0

#New entries for packet writing. Sept.2006:

/dev/pktcdvd/0 /media/cdvdwriter udf user,noauto,noatime,utf8 0 0
/dev/pktcdvd/1 /media/cdwriter udf user,noauto,noatime,utf8 0 0

[COLOR="Magenta"]I'm afraid I messed up. The "Computer - File Browser" shows 4 optical drives now:[/COLOR]
1) CD-RW drive
2) CD-RW/DVD+/-R drive
3) cdwriter
4) cdvdwriter
CD-RW and CD-RW/DVD drives can be opened, but not cdwriter and cdvdwriter.

I checked "/var/log/syslog" and got lots of messages like:
 
Sep 8 08:00:54 localhost kernel: [49317.123078] cdrom: open failed.

Sep 8 08:02:50 localhost kernel: [49381.682978] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'LinuxUDF', timestamp 2006/09/04 11:40 (1e5c)

Sep 8 08:03:15 localhost kernel: [49395.875328] hda: command error: status=0x51 { DriveReady SeekComplete Error }
Sep 8 08:03:15 localhost kernel: [49395.875335] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Sep 8 08:03:15 localhost kernel: [49395.875339] ide: failed opcode was: unknownSep 8 08:03:15 localhost kernel: [49395.875342] end_request: I/O error, dev hda, sector 1280
Sep 8 08:03:15 localhost kernel: [49395.875345] Buffer I/O error on device hda, logical block 320
Sep 8 08:03:52 localhost kernel: [49416.181746] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'LinuxUDF', timestamp 2006/09/04 11:40 (1e5c)

Sep 8 08:04:38 localhost kernel: [49441.789939] cdrom: hdb: mrw address space DMA selected
Sep 8 08:04:38 localhost kernel: [49441.800567] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Sep 8 08:04:38 localhost kernel: [49441.800573] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }

[COLOR="Magenta"]I'm lost, please help![/COLOR][/QUOTE]

---

### Post by monktbd on 2006-09-11
my guess is that the gnome-volume-manager mounts them automatically then.

check the removeable drives section in the system->preferences menu.

---

### Post by Cariboo1938 on 2006-09-11
> **monktbd said:**
> my guess is that the gnome-volume-manager mounts them _automatically_ then.Thanks monktbt, 
You are right, it mounts automatically when I insert a formatted CD. 
In my case I have a DVD/CD-RW combo drive (hda) and a standard CD-RW drive (hdb) installed. 
Putting a formatted CD in drive hda I get "dvdrecorder"  entered in /media.
Putting a formatted CD in drive hdb I get "cdrecorder" entered in /media. 
In both cases, when I try to open the CD, I get the message:> The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "dvdrecorder" / "cdrecorder".This makes sense too, because I didn't enable all owners yet. 'dradul' recommends in his HOW-TO to make the CD/DVD-RW writable to other users: *sudo chown /your/mount/point/.* Now, I guess the mount point in my case would be : */media/dvdrecorder* or */media/cdrecorder* 
If I apply this command line, I can see that the owner is changed from root to 777, but I still get the message (see above Quote)
[COLOR="Blue"]Do you have any idea how to make the CD-read/write feature a permanent addition to my system?[/COLOR]

---

### Post by monktbd on 2006-09-12
i dont know anything about packet writing in linux.
i just tried packet writing a couple of times years ago under windows and thought it was unstable and crap - lol. 
so i never touched it again and used normal burning then.

i am not sure how linux handles packet writing then.
you surely need some kind of rights to access it.
also i dont know whether gnome-volumen-manager disturbs the packet writing when it mounts the drives twice.
disabling the automount for the gnome-volume-manager might help.

as for the right to read/write on the burner:
you shoould maybe chown the group of the folder to a certain group that you put everyone n who should be able to burn with the devices and set the permissions like 775 which gives owner and group all the rights.
i also dont know whether the device itself and not only the directory needs to have these permissions itself.

---

### Post by Cariboo1938 on 2006-09-18
:-\" Case closed!...Packet Writing works...[COLOR="SeaGreen"]Attn.: This is valid for Ubuntu 6.06![/COLOR]

I had to mount a CD and not the CD drive, because the CD has the File System on it I wanted to use...UDF.
The solution is:
When executing the command
Code:
*sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0*

the formatted CD has to be inserted in the corresponding drive!Knowing this you can follow [dradul's HowTo]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=dradul") by the letter.

---

