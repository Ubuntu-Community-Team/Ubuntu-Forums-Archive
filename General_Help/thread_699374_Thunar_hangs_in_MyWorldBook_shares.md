---
title: "Thunar hangs in MyWorldBook shares"
date: 2008-02-17
forum: General Help
---

### Post by petsraibe on 2008-02-17
i'm using xubuntu GG on 1.6MHz/256MB system and after a little struggle (updating fstab) i can see my shares on WD MyWorldBook (uses Samba). I can browse folders and copy files in terminal window, I can even stream a movie with VLC but Thunar will hang after i browse the mounted folders. 'i tried to open  System Monitor but it hanged too.
So how to make thunar work with (large) network folders or/and how to get rid of the frozen applications.

Best wishes,

Peeter.

EDIT: works fine on xubuntu 6.0 LTS :)

---

### Post by wangvs80 on 2008-05-26
Petsraibe,

Could you please share the string you used in your fstab to map to the Myworldbook? (and anything else a newbie would have to do)  I have tried many combinations. My current is '//mybookworld/public /media/mountname  ntfs defaults 0 0'   I already mkdir a mountname directory.  The error message when I do 'mount -a' is 'ntfs-3g: Failed to access volume '//mybookworld/public': No such file or directory'

I have two other Vista machines that backup regularly to this device using a mapped drive over a wired lan.   My ubuntu internet and email work fine so I know I am getting to the network. ubuntu 8.04.  


Thanks,
Nancy

---

