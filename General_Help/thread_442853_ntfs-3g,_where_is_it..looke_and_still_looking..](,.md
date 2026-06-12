---
title: "ntfs-3g, where is it?..looke and still looking..	](*,). [Resolved]"
date: 2007-05-13
forum: General Help
---

### Post by downloaderx on 2007-05-13
want to access my 144 gb ntfs drive(xp) , and looked for this app. but don't seem to know where it is,have 6.06 dual booted on a seperate 40 gb drive.the ntfs has all my vids and tv shows. that i will show on the big screen via vid card
](*,)

---

### Post by thelinuxguy on 2007-05-14
Its a filesystem driver. You can get it from the downloads section at [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
The thread at [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009), linked from [www.ntfs-3g.org](www.ntfs-3g.org) has detailed instructions.

---

### Post by aysiu on 2007-05-14
This might help:
[HOWTO: NTFS with read/write support using ntfs-3g (easy method)](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by strabes on 2007-05-14
You simply have to install ntfs-3g and mount the ntfs drive as filesystem type "ntfs-3g" in your /etc/fstab. For example this is the line for my windows partition in my /etc/fstab: > /dev/sda1 /media/windows  ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1

Although your line could be as simple as: > /dev/sda1   /media/windows  ntfs-3g    defaults      0       0

---

### Post by aysiu on 2007-05-14
> **strabes said:**
> You simply have to mount an ntfs drive as filesystem type "ntfs-3g" in your /etc/fstab. For example this is the line for my windows partition in my /etc/fstab: 

Although your line could be as simple as:
You don't have to install *ntfs-3g* first?

---

### Post by mjitkop on 2007-05-14
I found it easier for me to use the "Add/Remove..." from the "Applications" menu (see screen shot) :)

---

### Post by kalpik on 2007-05-14
sudo apt-get install ntfs-config and then applications->system tools->NTFS config tool and just put a check there :)

---

### Post by strabes on 2007-05-14
> **aysiu said:**
> You don't have to install *ntfs-3g* first?

Well, yes you do. I thought it was assumed. I'll add that step into my post...

---

### Post by downloaderx on 2007-05-14
thanx for the nfo,, is helping greatly...and so far so good ,,

---

