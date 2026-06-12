---
title: "mount command not working from rc.local"
date: 2014-05-10
forum: General Help
---

### Post by pabc on 2014-05-10
I have the following in my /etc/rc.local

```
date > /home/phil/test.txt
sleep 30
echo 'pre-mount' >> /home/phil/test.txt
mount -t cifs //192.168.1.106/public -o auto,iocharset=utf8,file_mode=0775,dir_mode=0777 /NAS
echo 'post-mount' >> /home/phil/test.txt
```

and /home/phil/test.txt contains
```
Sat May 10 16:36:04 BST 2014
pre-mount
```

yet if I run 

```
sudo mount -t cifs //192.168.1.106/public -o auto,iocharset=utf8,file_mode=0775,dir_mode=0777 /NAS
```

everything mounts fine.

Why doesn't the rc.local script complete? I've done longer scripts and network is up prior to the mount command running

---

### Post by tomearp on 2014-05-10
You might like to try using [fstab]("https://help.ubuntu.com/community/Fstab") instead. There is a [Ubuntu wiki]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") page on how to auto mount cifs shares using fstab that may also be of interest.

---

### Post by pabc on 2014-05-12
I was initially using an fstab entry but it never mounted and I pressumed due to the network not being up when the fstab entries where processed. I know the fstab entry worked in theory as if i ran sudo mount -a after network was connected /NAS was populated.

Hence trying this approach.

---

### Post by SeijiSensei on 2014-05-12
Unless you define the networking interfaces in [/etc/network/interfaces]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html"), there will not be a network connection available at the time rc.local is run.  The Ubuntu default is to have the user start the network from the desktop. 

I've found that mounts defined in /etc/fstab do become active once the network is started from the desktop.  

Another option is to tell Ubuntu to [run the mount command when the network starts](http://ubuntuforums.org/showthread.php?t=1786173&p=10957361&viewfull=1#post10957361).

---

### Post by pabc on 2014-05-15
thank you - I'll try that

---

