---
title: "Question about rdiff-backup"
date: 2020-04-28
forum: General Help
---

### Post by Alligator on 2020-04-28
I'm trying to backup /home by itself, the whole drive minus /home and the other HD on a desktop to a USB drive.  First step /home see below.  Question: what am I missing with this. I need to make sure I have a backup before moving on to the next upgrade. Currently at 18.04LTS
```


Backing up /home, so I thought. 

ron@localhost:~$ sudo ln -s /media/ron/5be7881c-212d-44a4-ae3b-bb4677366bc7 HomeBackup
ron@localhost:~$ sudo rdiff-backup /home HomeBackup/Ron-home.backup
[sudo] password for ron: 


ron@localhost:~$ cd HomeBackup
ron@localhost:~/HomeBackup$ ls
Back_up  cdrom  home            lib         media  proc             run   srv       tmp  vmlinuz
bin      dev    initrd.img      lib64       mnt    Ron-home.backup  sbin  swapfile  usr  vmlinuz.old
boot     etc    initrd.img.old  lost+found  opt    root             snap  sys       var

Looks like the whole drive

ron@localhost:~/HomeBackup$ ls -ld Ron-home.backup
drwxr-xr-x 5 root root 4096 Mar 22  2019 Ron-home.backup


ron@localhost:~/HomeBackup$ cd
ron@localhost:~$ cd /
ron@localhost:/$ ls
bin    Data  home            lib         media  proc  sbin  swapfile  usr      vmlinuz.old
boot   dev   initrd.img      lib64       mnt    root  snap  sys       var
cdrom  etc   initrd.img.old  lost+found  opt    run   srv   tmp       vmlinuz
ron@localhost:/$ cd HomeBackup
bash: cd: HomeBackup: No such file or directory

Looks like the ln is gone.


ron@localhost:/$ cd /media/ron/5be7881c-212d-44a4-ae3b-bb4677366bc7
ron@localhost:/media/ron/5be7881c-212d-44a4-ae3b-bb4677366bc7$ ls
Back_up  cdrom  home            lib         media  proc             run   srv       tmp  vmlinuz
bin      dev    initrd.img      lib64       mnt    Ron-home.backup  sbin  swapfile  usr  vmlinuz.old
boot     etc    initrd.img.old  lost+found  opt    root             snap  sys   


```

---

