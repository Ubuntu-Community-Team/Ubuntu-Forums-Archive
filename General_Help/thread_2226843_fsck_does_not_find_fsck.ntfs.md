---
title: "fsck does not find fsck.ntfs"
date: 2014-05-29
forum: General Help
---

### Post by fernandojosecabral on 2014-05-29
I am trying to fix a pendrive that went kaput. But fsck complains about not finding fsck.ntfs.
I can't figure out how to make this command available. Any hints?

```
HP-ENVY-dv7 ~ # fsck /dev/sdb1
fsck de util-linux 2.20.1
fsck: fsck.ntfs: não encontrado
fsck: erro 2 ao executar fsck.ntfs para /dev/sdb1
HP-ENVY-dv7 ~ # 
HP-ENVY-dv7 ~ # 
HP-ENVY-dv7 ~ # whereis fsck.ntfs
fsck: /sbin/fsck.jfs /sbin/fsck.ext3 /sbin/fsck.minix /sbin/fsck.nfs /sbin/fsck.xfs /sbin/fsck.ext2 /sbin/fsck.ext4 /sbin/fsck.ext4dev /sbin/fsck /sbin/fsck.cramfs /sbin/fsck.msdos /sbin/fsck.vfat /sbin/fsck.reiserfs /usr/share/man/man8/fsck.8.gz


```

---

### Post by zteam2 on 2014-05-29
Hello!
I'm not sure there even exist a proper file system checker for NTFS in Linux.

But you can try this command

```
sudo ntfsck /dev/sda2/ 
```

Assuming your ntfs-drive is on /dev/sda2

If that's not working for you, you can try

```
sudo ntfsfix -b -d /dev/sda2/ 
```

Please note that ntfsfix is far more basic, than CHKDSK, it can only fix some very simple problems.

If none of this is working for you, you need re-create your USB-drive or run CHKDSK from a recovery disc or windows parttition.

Greetings.

---

### Post by jakke1975 on 2014-05-29
Check this thread perhaps?
[http://ubuntuforums.org/showthread.php?t=881344](http://ubuntuforums.org/showthread.php?t=881344)

---

### Post by fernandojosecabral on 2014-05-31
It seems the problem has to do with grsync. After trying several times, I found out that after running grsync to send files to the pendrive formated as ntfs, the pendrive goes kaput.
Now, one thing that is strange is that sync (unix sync) does not work either. It hangs up. That machine does not freeze, but I open a terminal, I run sync and the terminal hangs up (together with sync itself.) Does not matter if I run it as root or as an ordinary user. Ejecting the pendrive using any means does not work either. I always get the message "operation pending" (it does not matter if I try to eject before or after syncing.

I did not have problem using freefilesync to copy files, so, for the time being, I think the problem has to do with grsync.

updating ADENDUM

Nope! grsync is not the problem. There is something down deep bellow. The NTFS pendrive kept working find until I copied some files into it using nemo's drag and drop. When it finished copying
the files, the pendrive went kaput again. Same symptoms: sync does not work, pendrive can not be ejected, pendrive file are lost...

Now, if ntfs is the problem, than why freefilesync works?

---

### Post by oldfred on 2014-06-01
Paths too long or illegal characters?

I used to have the path too long on some files when writing to DVDs for backups. I think now it just tuncates.

And if you mount a NTFS partition it is better to exclude the illegal chars.
 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

