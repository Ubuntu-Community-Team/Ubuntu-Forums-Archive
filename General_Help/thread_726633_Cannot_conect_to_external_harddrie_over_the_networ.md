---
title: "Cannot conect to external harddrie over the network"
date: 2008-03-16
forum: General Help
---

### Post by Peneus on 2008-03-16
Hello,

I am using Hardy. I used to be able to connect to my external hard drive that is connected to another computer over the local  network. Now when try the same command which is 
 
"sudo mount 192.168.1.xxx:/media/<harddisk name> ~/extdisk"

I get the following error:

       "missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Any ideas?

Thanks

---

### Post by DoctorMO on 2008-03-17
is it an nfs mount or some other networking protocol such as windows file services (smb)? nfs should just require the addition of -type=nfs to the command line you tried.

---

### Post by Peneus on 2008-03-17
Thanks for your response DoctorMO,
I tried with --type=nfs option this time. But still no luck. this is what i am getting. 

$ sudo mount --type=nfs 192.168.1.xxx:/media/<disk name> ~/extdisk
mount: wrong fs type, bad option, bad superblock on 192.168.1.xxx:/media/<disk name>,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I am trying exactly what I did before. So i am surprised that it doesn't work anymore.  

Thanks

---

### Post by Peneus on 2008-03-21
I installed nfs-common and now it works.

---

