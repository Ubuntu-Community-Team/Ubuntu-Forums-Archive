---
title: "Mount Dual-Boot Windows NTFS fstab permissions"
date: 2013-12-02
forum: General Help
---

### Post by amhainen on 2013-12-02
My computer is dual booted with Ubuntu 13.10 x64 and Windws 7 x64. I edited my /etc/fstab to include my Windows partition:

```
UUID=[###]    /home/me/w7    ntfs-3g    defaults,locale=en_US.UTF-8      0   0
```

I didn't have many permissions for most of my files in Ubuntu (I could access a few folders, but not many). So I did [this]("http://stackoverflow.com/questions/3740152/how-to-set-chmod-for-a-folder-and-all-of-its-subfolders-and-files-in-linux-ubunt"), luckily only to my Windows user folder and NOT the Windows root:

[http://stackoverflow.com/questions/3740152/how-to-set-chmod-for-a-folder-and-all-of-its-subfolders-and-files-in-linux-ubunt](http://stackoverflow.com/questions/3740152/how-to-set-chmod-for-a-folder-and-all-of-its-subfolders-and-files-in-linux-ubunt)

```
find /home/me/w7/Users/me -type d -exec chmod 777 {} \;
```
```
find /home/me/w7/Users/me -type f -exec chmod 777 {} \;
```

That made everything work in Ubuntu fine. I had read and write and I don't really care about the executable flag (I'm not very good with Linux...I just set all the flags and don't worry about security).

I logged back into Windows and everything seemed fine. I downloaded a new install for a program to C:\Users\me\Downloads\installer.exe. The problem is that I ran into this:

[IMG]http://i.imgur.com/RUNuyDs.png[/IMG]

What happened was that a Deny flag was set for everything in my Windows user folder. Again, luckily I only did this to my user folder and not the Windows root! I removed the Deny flag for everything (including checking the box for all sub folders) and Windows was fine.

I'm back in Linux now and I don't have any permissions for my Windows files (back to square 1). I tried [this]("http://www.psychocats.net/ubuntu/mountwindows") thread using the NTFS Configuration Tool to add write for everything, but still no luck.

**What is the proper way to mount my Windows NTFS partition to that I have read, write, and execute (or really equivalent permissions as set in Windows) for my Windows files?**

Everything on Windows is fine, just would like to have permission in Ubuntu.

Thanks for the help!

---

### Post by oldfred on 2013-12-02
I have seen this as a suggested entry:

 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

The umask of 000 is 777 permissions.

---

### Post by amhainen on 2013-12-02
> **oldfred said:**
> I have seen this as a suggested entry:

 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

The umask of 000 is 777 permissions.

Works fine with that line!

```
UUID=[###]    /home/me/w7    ntfs-3g    defaults,nls=utf8,umask=000,uid=1000,windows_names    0    0
```

I gues that umask of 000 = 777 is the key. What is uid=1000?

Thanks!!

---

### Post by oldfred on 2013-12-02
uid is user id. With Debian based systems your default user id is 1000 and various system ids exist.
for me:
 uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),116(fuse),127(sambashare)



fstab is backwards, so a umask of 000 is 777 permissions and 777 is no permissions at all.
And NTFS does not support ownership nor permissions, so only the fstab setting is the default.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

