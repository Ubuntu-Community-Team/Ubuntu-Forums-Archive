---
title: "Execute a Shell Script on a Removable Drive?"
date: 2014-03-05
forum: General Help
---

### Post by BuntuSeriously on 2014-03-05
Hello folks!  

I have a shell script which I'd like to set as executable on a thumb drive; and the checkbox setting in file properties won't take.

Without chmodding each file from the command line, is there a system setting which I can trip that will allow me to set files on removable media as executable???

Running 12.04 today . . .

Thanks!

---

### Post by steeldriver on 2014-03-05
What is the filesystem on the drive, and how are you mounting it (via fstab, or relying on the default udisks automount?)

---

### Post by BuntuSeriously on 2014-03-05
@steeldriver:

FS is FAT32; and the mount up is entirely automated through XFCE/Thunar (have no idea what the underlying processes are; as they are concealed).

Plug & play . . .

---

### Post by Vaphell on 2014-03-05
FAT is incopatible with linux permissions so no, not really

you need to run the script by calling the shell explicitly and passing the file as a param to remove the need for the +x bit.
```
bash scriptname.sh
```

---

### Post by BuntuSeriously on 2014-03-05
@Vaphell:

Was in a hurry: Must've done everything but that.  Thanks, also, for the insight...

Have a great day, all.

---

### Post by BuntuSeriously on 2014-03-05
Actually, there's still a problem here:

Shell scripts _*will*_ execute on a FAT32-formatted flash (thumb) drive after all.  This was verified via Parted Magic: Same files, same drive, execute without issue ;)

It seems as though this particular phenomena (disallowing attribute executable for files on a thumb drive) is an Ubuntu/Xubuntu setup issue of some sort --

So, without chmodding, what's the secret handshake to cut this problem loose?

Any ideas???


Thanks again!

---

### Post by Vaphell on 2014-03-05
at the mount time a blanket set of permissions is applied to the whole non-linux partition to make it sort of compatible with linux and transparent to programs dealing with files and dirs. If your drive got automagically mounted with +x bit set, then yes, shell scripts will be marked executable, as will all other files. Chmodding won't work however.

To configure how drives are mounted look into the fstab file, specifically the umask setting.

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)
[http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab](http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab)

---

### Post by BuntuSeriously on 2014-03-06
@Vaphell:

Thanks again!  I'll fiddle with fstab & come back with the upshot --

:cool:

---

