---
title: "Error when run &quot;sudo apt update&quot;"
date: 2023-05-02
forum: General Help
---

### Post by lovenguyen on 2023-05-02
I installed ubuntu 23.04 . When I run "sudo apt update", I get a lot of information: 
et:1 file:/cdrom lunar InRelease
Ign:1 file:/cdrom lunar InRelease
Get:2 files:/cdrom lunar Release
Err:2 files:/cdrom lunar Release
   File not found - /cdrom/dists/lunar/Release (2: No such file or directory)
Hit:3 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar InRelease
Reading package lists... Done
E: The repository 'file:/cdrom lunar Release' no longer has a Release file.
N: Updating from such a repository can't be done secure, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
How can I fix this problem??

---

### Post by Bashing-om on 2023-05-02
lovenguyen; Hey --

Please post back the output from terminal command:
```

cat -n /etc/apt/sources.list

```
- Between code tags -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we see if the CD source is enabled.

[INDENT]all in the process
[/INDENT]

---

### Post by lovenguyen on 2023-05-03
ok. thanks. I have installed ubuntu again and no problem because of it.

---

### Post by Impavidus on 2023-05-03
Fixing this would have taken about 10 seconds.

Could you mark the thread as solved?

---

### Post by lovenguyen on 2023-05-03
ok thanks

---

### Post by lovenguyen on 2023-05-03
> **Bashing-om said:**
> lovenguyen; Hey --

Please post back the output from terminal command:
```

cat -n /etc/apt/sources.list

```
- Between code tags -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we see if the CD source is enabled.
[INDENT]all in the process
[/INDENT]


I just ran "sudo apt update" and it shows an error sudo apt update
 Hit:1 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) lunar InRelease                    
Get:3 [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) lunar-updates InRelease [90.7 kB]  
Hit:4 [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) lunar-backports InRelease          
Get:5 [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) lunar-security InRelease [90.7 kB] 
Ign:6 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable InRelease                   
Hit:7 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable Release                     
Hit:8 [https://ppa.launchpadcontent.net/bamboo-engine/ibus-bamboo/ubuntu](https://ppa.launchpadcontent.net/bamboo-engine/ibus-bamboo/ubuntu) lunar InRelease
Ign:10 [https://ppa.launchpadcontent.net/ubuntu-vn/ppa/ubuntu](https://ppa.launchpadcontent.net/ubuntu-vn/ppa/ubuntu) lunar InRelease
Err:11 [https://ppa.launchpadcontent.net/ubuntu-vn/ppa/ubuntu](https://ppa.launchpadcontent.net/ubuntu-vn/ppa/ubuntu) lunar Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/ubuntu-vn/ppa/ubuntu lunar Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
I ran "cat -n /etc/apt/sources.list" and then typed "sudo apt update" and it still shows the same error. What is it?

---

### Post by Bashing-om on 2023-05-03
lovenguyen - Well !

When we look a at the source for that PPA:
[https://ppa.launchpadcontent.net/ubuntu-vn/ppa/ubuntu/dists/](https://ppa.launchpadcontent.net/ubuntu-vn/ppa/ubuntu/dists/)
one sees that the app has had no love in a long time; is no longer supported.

Remove that source from the system.

-all good things do end -

---

### Post by lovenguyen on 2023-05-04
ok thanks

---

