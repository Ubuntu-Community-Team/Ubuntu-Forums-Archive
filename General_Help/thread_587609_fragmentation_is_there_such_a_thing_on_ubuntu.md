---
title: "fragmentation is there such a thing on ubuntu?"
date: 2007-10-22
forum: General Help
---

### Post by tynen on 2007-10-22
II don't know if there is such a thing on unix/linux. If there is what forms of fighting it are there? On windows I use DirMS (do it right microsoft) it's a fragmentation tool. 

What sort of maintenance is necessary for Ubuntu? 

I know it's stable and all that, but it's gotta get messy some where..right?

---

### Post by Shazaam on 2007-10-22
Ubuntu uses a journalizing file system so there  is no REAL need to defragment like with Windows.
Ubuntu will take care of itself quite nicely.

---

### Post by seventyeights on 2007-10-22
The short answer is that linux filesystems arrange the data across the platters more efficiently, and do not need to be defragged.

For more, check out this explanation:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

---

### Post by Inxsible on 2007-10-22
Yes there is fragmentation. But its not because of the OS that you use. its the file system that the OS uses. Maybe, Microsoft is not at fault in this case, except maybe for its choice of file system. ( Of course, MS has designed the NTFS file system, so the fault comes back to them ;) )

Anyway, lall file systems suffer from fragmentation. But ike others have pointed out. Linux file systems like EXT3, EXT4, reiserfs etc are journaled and the fragmentation is very less and doesn't really affect performance much.

---

### Post by tynen on 2007-10-23
Before any of you guys posted I looked for a way to defrag (bad idea) I ran the command and I knew I was deep in it, before it was too late. All my programs stop responding so I rebooted. Once I (attempted) to reboot Ubuntu won't load, and it goes to a terminal like full screen mode.. HELP!!! ><

The command was "fsck" and it kept asking me questions, and i kept saying yes.. becuase I'm stupid.. and i thought it was defragging.. lol, I got all happy and hastey.  >< gosh I'm stupid . lol don't mess with stuff so fundamental especially when you don't know what you're doing..

---

### Post by pointone on 2007-10-23
Running fsck on a mounted volume will result in data loss / corruption. Not sure if it's possible to recover. Try running fsck from a live CD and make sure nothing's mounted!

---

### Post by tynen on 2007-10-23
> **pointone said:**
> Running fsck on a mounted volume will result in data loss / corruption. Not sure if it's possible to recover. Try running fsck from a live CD and make sure nothing's mounted!

How do you run fsck on a drive that isn't mounted??

---

### Post by scorp123 on 2007-10-23
> **tynen said:**
> How do you run fsck on a drive that isn't mounted?? You never ever run fsck on a filesystem that is mounted. Never! As for using fsck ... all you need to know is the device name, e.g. /dev/sda1, /dev/sda2 and so on (those should be the same as in your /etc/fstab file). So you could boot from a Live CD and then have the live CD session check on your harddisks (e.g. if they failed for some reason). ```
sudo fsck /dev/sda1
```

There is a manual to everything on UNIX + Linux with all the details: ```
man fsck
``` (... use your cursor keys to navigate the manual, PgUp + PgDown jump one page forward and backward, and you use the "Q" key to quit).

---

### Post by tynen on 2007-10-23
> **scorp123 said:**
> You never ever run fsck on a filesystem that is mounted. Never! As for using fsck ... all you need to know is the device name, e.g. /dev/sda1, /dev/sda2 and so on (those should be the same as in your /etc/fstab file). So you could boot from a Live CD and then have the live CD session check on your harddisks (e.g. if they failed for some reason). ```
sudo fsck /dev/sda1
```

There is a manual to everything on UNIX + Linux with all the details: ```
man fsck
``` (... use your cursor keys to navigate the manual, PgUp + PgDown jump one page forward and backward, and you use the "Q" key to quit).

Didn't work. Thank you though.. ;_; I'll just have to rebuild.

---

### Post by Soarer on 2007-10-23
How do you mean 'it didn't work'?

If you can give us a little more information (like, what error was reported) it' possible you could save it.

---

### Post by Nunu on 2007-10-23
ah to be young. I remember my first encounter with fsck... it twas not pretty. I also rebuild the machine in the end, because i didn't know you could fix it from the live CD

---

