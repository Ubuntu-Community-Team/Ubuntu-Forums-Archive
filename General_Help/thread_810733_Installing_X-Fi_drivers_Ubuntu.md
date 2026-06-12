---
title: "Installing X-Fi drivers Ubuntu"
date: 2008-05-28
forum: General Help
---

### Post by Deverell on 2008-05-28
Hello,
I've been following the instructions of this [thread]("http://ubuntuforums.org/showpost.php?p=4874981&postcount=2").

I'm having problems with instruction 6. After I type in the command I get this in the terminal. 
```
dpkg-split: error reading oss-linux_v4.0-1015_amd64: Is a directory
dpkg: error processing oss-linux_v4.0-1015_amd64 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 oss-linux_v4.0-1015_amd64

```

I'm using Hardy Heron (64), and I have a AMD 64 CPU. I'm not a proficient linux user. Any help much appreciated.
Thanks,

Dev

---

### Post by Deverell on 2008-05-29
I've gotten by the above problem I was applying the command to the extracted file not the deb file. Anyway the new problem is instruction is still number six. It's from the above mentioned thread. This is what I'm getting.

```
sean@sean-desktop:~/Desktop$ sudo dpkg -i oss-linux_v4.0-1015_amd64.deb
[sudo] password for sean: 
(Reading database ... 109150 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1015 (using oss-linux_v4.0-1015_amd64.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1015_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.24-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/lib/oss/etc/devices.list: No such file or directory
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1015_amd64.deb

```

Any help or advice would be much appreciated, I really want to get Ubuntu working or at least give it a decent attempt. I genuinely don't want to go back to Windows.
Thanks,
Dev

---

