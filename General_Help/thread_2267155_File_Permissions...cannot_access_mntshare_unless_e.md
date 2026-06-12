---
title: "File Permissions...cannot access /mnt/share unless execute permission is set?!"
date: 2015-02-27
forum: General Help
---

### Post by KillerKelvUK on 2015-02-27
I've a clean install of 14.10, I mount several volumes into /mnt and so have been rebuilding and noticed this oddity...would appreciate it someone can explain what I'm doing wrong or why my expectations are incorrect...basically I believe that if I either own a directory or am a member of the group the directory is owned by then with a basic READ permission I should be able to access said directory...right?

The below excerpt is off my live system...I create a 'test' directory under /mnt, alter the ownership so I own it but then I can only change into that directory if I set the execute bit for the user????

```

kelvin@blackserver:/mnt$ whoami
kelvin


kelvin@blackserver:/mnt$ ls -l
total 8
drwxrwx--- 10 kelvin       sambashare 4096 Feb 27 21:31 share
drwxrwx---  2 libvirt-qemu kvm        4096 Feb 27 21:45 vms


kelvin@blackserver:/mnt$ sudo mkdir test


kelvin@blackserver:/mnt$ sudo chown kelvin:kelvin test


kelvin@blackserver:/mnt$ chmod 600 test


kelvin@blackserver:/mnt$ ls -la
total 20
drwxr-xr-x  5 root         root       4096 Feb 27 22:04 .
drwxr-xr-x 22 root         root       4096 Feb 27 21:28 ..
drwxrwx--- 10 kelvin       sambashare 4096 Feb 27 21:31 share
drw-------  2 kelvin       kelvin     4096 Feb 27 22:04 test
drwxrwx---  2 libvirt-qemu kvm        4096 Feb 27 21:45 vms


kelvin@blackserver:/mnt$ cd test
bash: cd: test: Permission denied


kelvin@blackserver:/mnt$ chmod 700 test


kelvin@blackserver:/mnt$ cd test

kelvin@blackserver:/mnt/test$ ls -la
total 8
drwx------ 2 kelvin kelvin 4096 Feb 27 22:04 .
drwxr-xr-x 5 root   root   4096 Feb 27 22:04 ..



kelvin@blackserver:/mnt/test$ cd ..

kelvin@blackserver:/mnt$ ls -la
total 20
drwxr-xr-x  5 root         root       4096 Feb 27 22:04 .
drwxr-xr-x 22 root         root       4096 Feb 27 21:28 ..
drwxrwx--- 10 kelvin       sambashare 4096 Feb 27 21:31 share
drwx------  2 kelvin       kelvin     4096 Feb 27 22:04 test
drwxrwx---  2 libvirt-qemu kvm        4096 Feb 27 21:45 vms


```

---

### Post by sisco311 on 2015-02-27
It may not be obvious at first why do you need execute permission on a directory (and all its parent directories) in order to cd into it, but yes you need. ;)

For a detailed explanation please check out:  [http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm](http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm) (scroll down to the directories section)

---

### Post by KillerKelvUK on 2015-02-27
Well, I do feel a fool but suspected my expectations and thus understanding of file perms was wrong.  Thanks for the linked article.

Kind regards,

Kelvin

---

