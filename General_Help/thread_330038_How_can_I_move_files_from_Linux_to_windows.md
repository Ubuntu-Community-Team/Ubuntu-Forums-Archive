---
title: "How can I move files from Linux to windows?"
date: 2007-01-02
forum: General Help
---

### Post by motermouth on 2007-01-02
How could I make it so that in linux I can see my windows partition? I have installed gparted but how do I do the rest?

~Motermouth~

---

### Post by xmastree on 2007-01-02
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

### Post by earobinson on 2007-01-02
[QUOTE=motermouth]I'm sorry to bother you again but could you let me know if you know anything about this question... [http://www.ubuntuforums.org/showthread.php?t=330038]("http://www.ubuntuforums.org/showthread.php?t=330038")

Thanks[/QUOTE] No problem ... the link above should do it for you let us know if you need more help, 

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ntfs&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ntfs&titlesearch=Titles) can also help you if you get stuck

---

### Post by itsmonktastic on 2007-01-02
That will allow you to read all of your windows files in Ubuntu, but (I'm a bit new, but this is what I was lead to believe) you won't be able to move files from Linux to the NTFS partition, as it will be accessed as read only.

If that's what you're interested in, I suggest checking out:

[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

Which will allow you to read and write to your Linux partition from windows, or alternatively [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) which will only allow you to read the Linux files in windows(so copying will be possible).

---

### Post by earobinson on 2007-01-02
one more link [http://www.ubuntuforums.org/showthread.php?t=329693](http://www.ubuntuforums.org/showthread.php?t=329693)

---

### Post by bodhi.zazen on 2007-01-02
Mounting and permissions depends on the file system:

_Windows:_

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

Alternately you can use a CD/Flash drive.

If you move a file from Linux -> Windows you should scan it with antiviral software first.

---

