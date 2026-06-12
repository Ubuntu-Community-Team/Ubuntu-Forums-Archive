---
title: "hp pavilion zv5000 FAT32 mounting probelm"
date: 2007-03-03
forum: General Help
---

### Post by acwspoon on 2007-03-03
Hey, I put Ubuntu on my brothers computer and set it up just like mine.  I mounted his FAT32 hard drive by creating the directory /osshare and then editing the /etc/fstab by adding this...

/dev/hda2    /osshare    vfat    defaults,auto,utf8,umask=0000,gid=46    0    2

On my computer it worked and allowed write/read access but on his it will only allow read access.  I'm stumped on this because I'm new to the whole process and I really need Help.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Thanks in advance!

Also if a hp pavilion user answers this question... I also followed the broadcomm 43xx installation and now on his computer the wireless light doesn't come on and the entire eth1 disappeared, pretty confused on that as well. but more importantly for now is the mounting problem...

---

### Post by taurus on 2007-03-03
Change this one

```
/dev/hda2 /osshare vfat defaults,auto,utf8,umask=0000,gid=46 0 2
```

to 

```
/dev/hda2   /osshare   vfat   iocharset=utf8,umask=000   0   0
```
then, reboot.

---

### Post by acwspoon on 2007-03-03
Ok, I did that and now I can save files in the /osshare directory but the my documents folder where all his stuff is, is read only.  I went to the properties and it says the owner is "root" and that the it only an access file instead of mine, which is create and read.

When I change over to windows, My documents is also read only and when I try to change it to not read only and re check the properties it's back to read only again.

I'm severely confused..

Thanks again

---

### Post by Azakus on 2007-03-03
Do this
```
sudo chown yourusername: /osshare
```

---

### Post by acwspoon on 2007-03-03
this is what i got back after entering that


chown: changing ownership of `/osshare': Operation not permitted

the /osshare says I can create and delete files just not My documents

---

### Post by terry98 on 2007-03-04
> **acwspoon said:**
> this is what i got back after entering that


chown: changing ownership of `/osshare': Operation not permitted

the /osshare says I can create and delete files just not My documents

try "sudo chown youruser /osshare"

or

"sudo chmod a+rwx /osshare"

---

### Post by acwspoon on 2007-03-04
The My Documents folder still says I can only access files, not create and delete but in the /osshare I can create and delete files all I want.  Does it have something to do with windows since its the My Documents file?

---

