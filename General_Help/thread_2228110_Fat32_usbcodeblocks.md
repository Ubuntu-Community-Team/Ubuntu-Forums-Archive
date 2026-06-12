---
title: "Fat32 usb/codeblocks"
date: 2014-06-05
forum: General Help
---

### Post by awildo on 2014-06-05
Hello !,
I'm using a usb key to run all my programming codes and I had no problem when i was using windows at home/school. Now i've installed linux and when i try to execute codes with codeblocks it's showing error : "permission denied". This is happening cause you can't read/write on a fat32 usb in linux or smth like this.
Chmod doesn't allow to change permission on fat32 key, so i have to mount the usb key at start-up with all the good permissions but this is a pain. I've put :

UUID=9F51-234B /media/"myuser"/"nameofmykey" vfat user,umask=007,gid=46,uid=1000,rw,exec 0 0 
 

in fstab, it kinda works but it is asking me to insert my usb key at startup, if i don't it doesn't work.
What can i do to fix this?
Best way would be to automatically mount my key only when i'm inserting it with the permissions for my user to read/write/modify but i don't know how to do it.
Thanks in advance for your answers

---

### Post by steeldriver on 2014-06-05
Hello and welcome to the forums

I don't know how to change the mount options for user-mounted filesystems, but you could try adding the noauto option to your fstab entry to get rid of the startup messages

```

UUID=9F51-234B /media/"myuser"/"nameofmykey" vfat **noauto**,user,umask=007,gid=46,uid=1000,rw,exec 0 0

```

Then you should be able to manually mount the device after inserting it using
```

mount /media/"myuser"/"nameofmykey"

```

---

### Post by awildo on 2014-06-05
Oh nice, just had to add the "noauto" thanks !

---

