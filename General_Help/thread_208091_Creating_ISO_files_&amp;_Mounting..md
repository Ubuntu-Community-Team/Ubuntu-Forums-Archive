---
title: "Creating ISO files &amp; Mounting."
date: 2006-07-03
forum: General Help
---

### Post by Just4 on 2006-07-03
I want to be able to create data ISO files (Without having to burn the data) is there a way to do this? - In Windows I used WinImage, I'd also like to know of a way to mount ISO's (I used Daemon Tools in Windows) - Thanks for any help.

---

### Post by kaamos on 2006-07-03
Hello!

To create an iso from the dir cd_dir:
```
mkisofs -o cd.iso cd_dir
```

to mount the iso:
```
sudo mkdir /media/mount
sudo mount cd.iso /media/mount -o loop
```

mkisofs has a lot of available options, use "man mkisofs" to check them out if you need to.

---

### Post by aysiu on 2006-07-03
This screenshot shows how to create an ISO with K3B, but I'm sure the same can be done with Gnomebaker or Graveman.

How to mount an ISO:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)

---

### Post by Buffalo Soldier on 2006-07-03
In GNOME:[LIST]
[*] right click on your CD icon and select **Copy Disc...**
[*] select **Copy disc to: *File image***
[*] type your choice of name for the ISO file
[*] enjoy your drink
[/LIST]

---

### Post by FredB on 2006-07-03
- sigh - 

I don't know you could create that easily an ISO file with Nautilus :(

Maybe I am a little too addict with command line for this. Thanks for the tip !

---

