---
title: "I Lost My /home"
date: 2007-09-22
forum: General Help
---

### Post by Suhendri on 2007-09-22
Hi All..

My Desktop was ubuntu-edgy installed. I've splitted my harddisk to 3 partitions, as /, /home and swap file.

Since yesterday morning i cannot logging in to my desktop..:( The system looks normal from startup to logon screen appear.

So i start boot my desktop with recovery mode, i found this weirdness :
cannot initialize /etc/mtab

after logon using terminal mode using root password, seems everything OK. but when i changed directory to /home, that folder empty..:confused: I shocked.. cause all of my files and the others users on that folder...

i tried to ls /etc/mtab, but the response is ls: mtab input/output error

i tried to ls -l /etc and the response for mtab is : ?--------- ?  ?  ?  ?  ? mtab

Please help me how to solve my problem.... So i can get all of our files on /home folder..

---

### Post by dcstar on 2007-09-22
> **Suhendri said:**
> Hi All..

My Desktop was ubuntu-edgy installed. I've splitted my harddisk to 3 partitions, as /, /home and swap file.

Since yesterday morning i cannot logging in to my desktop..:( The system looks normal from startup to logon screen appear.

So i start boot my desktop with recovery mode, i found this weirdness :
cannot initialize /etc/mtab

after logon using terminal mode using root password, seems everything OK. but when i changed directory to /home, that folder empty..:confused: I shocked.. cause all of my files and the others users on that folder...

i tried to ls /etc/mtab, but the response is ls: mtab input/output error

i tried to ls -l /etc and the response for mtab is : ?--------- ?  ?  ?  ?  ? mtab

Please help me how to solve my problem.... So i can get all of our files on /home folder..

If you have a separate /home partition it is mounted on startup, if it isn't mounted (for any reason) then you will experience the problem you have described.

Check you /etc/fstab file and make sure that your /home partition is listed, then (in a terminal) do:

```
sudo fsck -y /dev/your-unmounted-home-partition-designation
```

This should fix any filesystem errors that my be preventing your /home partition from mounting on start up. Then reboot and see if things work.

---

### Post by Suhendri on 2007-09-23
Problem Solved..:D

What i have todo just remove the /etc/mtab and reboot the system..

Voila... the system back to normal

---

