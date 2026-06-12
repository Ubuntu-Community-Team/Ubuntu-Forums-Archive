---
title: "p click on update but nothing happens"
date: 2024-07-02
forum: General Help
---

### Post by ronjjjg8885 on 2024-07-02
even after entering the password..

is that a bug?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293934&stc=1[/IMG]

sorry. i meant to type..... "i click on update but nothing happens"

---

### Post by currentshaft on 2024-07-02
Try running "snap refresh" from the terminal.

---

### Post by ronjjjg8885 on 2024-07-02
even now, after running "snap refresh" [it said "All snaps up to date."] i can't update the software..[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293939&stc=1[/IMG]

---

### Post by ronjjjg8885 on 2024-07-04
do you have a solution?

---

### Post by Rubi1200 on 2024-07-04
Try this instead:

```
sudo killall snap-store
sudo snap refresh

```

---

### Post by ronjjjg8885 on 2024-07-04
i got this
```
sudo killall snap-store
[sudo] password for not-pc: 
Sorry, try again.
[sudo] password for not-pc: 
snap-store: no process found

```

---

### Post by Rubi1200 on 2024-07-05
What does this show?
```
ps aux | grep snap

```

---

### Post by ronjjjg8885 on 2024-07-05
[https://pastebin.com/dudUJjV6](https://pastebin.com/dudUJjV6)

---

### Post by Rubi1200 on 2024-07-05
Make sure any Ubuntu Software apps are closed and try this:
```
sudo snap refresh snap-store
```

---

### Post by ronjjjg8885 on 2024-07-05
```
sudo snap refresh snap-store
snap "snap-store" has no updates available
```

---

### Post by ronjjjg8885 on 2024-07-06
what does it mean?

---

### Post by Rubi1200 on 2024-07-07
It seems to suggest there are no updates at this time.

I actually don't use the Snap Store to update, only the terminal.

It is possible there is a phased update, which means you need to wait.

Are you still getting errors?

Try this:

```
sudo apt update && sudo apt upgrade
```

If is shows errors or says packages were held back/not updated, then please post that information here.

---

### Post by ronjjjg8885 on 2024-07-07
in the app center.. when cliking on the green button to update Thunderbird nothing happens after entering the password.

is this a known problem or is it just me?

```
sudo apt update && sudo apt upgrade
[sudo] password for not-pc: 
Hit:1 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:2 http://il.archive.ubuntu.com/ubuntu noble InRelease
Get:3 http://il.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Hit:4 http://il.archive.ubuntu.com/ubuntu noble-backports InRelease
Get:5 http://il.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [220 kB]
Get:6 http://il.archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [116 kB]
Fetched 462 kB in 2s (246 kB/s)   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libcjson1 libpostproc57 libavcodec60 libavutil58 libswscale7 libswresample4
  libavformat60 libavfilter9
Learn more about Ubuntu Pro at https://ubuntu.com/pro
#
# OpenSSH CVE-2024-6387 has been fixed for 22.04 LTS, 23.10 and 24.04 LTS.
# RegreSSHion: Possible RCE Due To A Race Condition In Signal Handling.
# For more details see: https://ubuntu.com/security/notices/USN-6859-1.
#
The following packages will be upgraded:
  libclang-cpp18 libclang1-18 libllvm18 ubuntu-pro-client
  ubuntu-pro-client-l10n
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 49.1 MB of archives.
After this operation, 722 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://il.archive.ubuntu.com/ubuntu noble-updates/main amd64 ubuntu-pro-client-l10n amd64 32.3.1~24.04 [19.4 kB]
Get:2 http://il.archive.ubuntu.com/ubuntu noble-updates/main amd64 ubuntu-pro-client amd64 32.3.1~24.04 [229 kB]
Get:3 http://il.archive.ubuntu.com/ubuntu noble-updates/main amd64 libclang-cpp18 amd64 1:18.1.3-1ubuntu1 [13.5 MB]
Get:4 http://il.archive.ubuntu.com/ubuntu noble-updates/main amd64 libllvm18 amd64 1:18.1.3-1ubuntu1 [27.5 MB]
Get:5 http://il.archive.ubuntu.com/ubuntu noble-updates/main amd64 libclang1-18 amd64 1:18.1.3-1ubuntu1 [7,803 kB]
Fetched 49.1 MB in 5s (10.2 MB/s)         
(Reading database ... 190335 files and directories currently installed.)
Preparing to unpack .../ubuntu-pro-client-l10n_32.3.1~24.04_amd64.deb ...
Unpacking ubuntu-pro-client-l10n (32.3.1~24.04) over (32.3~24.04) ...
Preparing to unpack .../ubuntu-pro-client_32.3.1~24.04_amd64.deb ...
Unpacking ubuntu-pro-client (32.3.1~24.04) over (32.3~24.04) ...
Preparing to unpack .../libclang-cpp18_1%3a18.1.3-1ubuntu1_amd64.deb ...
Unpacking libclang-cpp18 (1:18.1.3-1ubuntu1) over (1:18.1.3-1) ...
Preparing to unpack .../libllvm18_1%3a18.1.3-1ubuntu1_amd64.deb ...
Unpacking libllvm18:amd64 (1:18.1.3-1ubuntu1) over (1:18.1.3-1) ...
Preparing to unpack .../libclang1-18_1%3a18.1.3-1ubuntu1_amd64.deb ...
Unpacking libclang1-18 (1:18.1.3-1ubuntu1) over (1:18.1.3-1) ...
Setting up ubuntu-pro-client (32.3.1~24.04) ...
Installing new version of config file /etc/apparmor.d/ubuntu_pro_esm_cache ...
Setting up libllvm18:amd64 (1:18.1.3-1ubuntu1) ...
Setting up ubuntu-pro-client-l10n (32.3.1~24.04) ...
Setting up libclang1-18 (1:18.1.3-1ubuntu1) ...
Setting up libclang-cpp18 (1:18.1.3-1ubuntu1) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.2) ...
not-pc@not-pc:~$ 




```

even after putting the command i get the thunderbird listed in the software center.....

weird.. isn't it?

tnx

---

### Post by gividen on 2024-07-08
[IMG]https://ibb.co/fxcS0XR[/IMG][https://ibb.co/fxcS0XR](https://ibb.co/fxcS0XR)[IMG]https://ibb.co/fxcS0XR[/IMG]
I am running Ubuntu 22.04.4 LTS and having a similar problem.

> $ sudo apt update && sudo apt upgradeHit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [128 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [129 kB]
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease 
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages [1,791 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main i386 Packages [654 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages [1,101 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/universe i386 Packages [716 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main i386 Packages [497 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/universe Translation-en [255 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 Packages [1,583 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe amd64 Packages [883 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe i386 Packages [616 kB]
Fetched 8,354 kB in 2s (4,453 kB/s)                        
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
11 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libwpe-1.0-1 libwpebackend-fdo-1.0-1 nvidia-firmware-535-535.154.05
Use 'sudo apt autoremove' to remove them.
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libpostproc55 libavcodec58 libavutil56 libswscale5 libswresample3
  libavformat58 libavfilter7
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages have been kept back:
  python3-update-manager ubuntu-desktop ubuntu-desktop-minimal ubuntu-minimal
  ubuntu-standard update-manager update-manager-core xserver-common
  xserver-xephyr xserver-xorg-core xserver-xorg-legacy
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.



[IMG]https://ibb.co/fxcS0XR[/IMG]

---

