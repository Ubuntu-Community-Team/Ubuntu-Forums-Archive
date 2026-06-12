---
title: "Using Dislocker to access Bitlocked Hard drive"
date: 2014-06-17
forum: General Help
---

### Post by 0pt1cKill3r on 2014-06-17
Hello everyone. Im having problems and i cant boot on my windows 8.1 and i decided to backup everything to my other hard drive using a live Ubuntu usb so i could make a fresh install of Windows OS. After launching Ubuntu i noticed that i couldnt access my other Hard drive because it is bitlocked (i have a backup of bitlocker recovery key). 

So i searched around and found out that there was a program named *dislocker* which could decrypt and give me read/write access to my HD.Downloaded it from [here]("http://www.hsc.fr/ressources/outils/dislocker/download/") (i think its the last version) and tried to install using install.txt and [this page]("http://earthwithsun.com/questions/376533/how-to-access-bitlocker-encrypted-drive-in-linux")(i should mention i just have some basic knowledge of Linux OS). installed correctly and than tried to use it.
Here is what i get :

```

ubuntu@ubuntu:/usr/bin$ [B]sudo dislocker -r -V /dev/sdb -p670318-245916-523534-119658-014135-683518-341990-623590 --/media/windows

[/B]dislocker: unrecognized option '--/media/windows'
Usage: dislocker [-hqrv] [-l LOG_FILE] [-o OFFSET] [-V VOLUME DECRYPTMETHOD -F[N]] [-- ARGS...]
    with DECRYPTMETHOD = -p[RECOVERY_PASSWORD]|-f BEK_FILE|-u[USER_PASSWORD]|-k FVEK_FILE|-c
 (v0.3)
Options:
    -c, --clearkey        decrypt volume using a clear key (default)
    -f, --bekfile BEKFILE
                          decrypt volume using the bek file (on USB key)
    -F, --force-block N   force use of metadata block number N (1, 2 or 3)
    -h, --help            print this help and exit
    -k, --fvek FVEK_FILE  decrypt volume using the FVEK directly
    -l, --logfile LOG_FILE
                          put messages into this file (stdout by default)
    -o, --offset OFFSET   BitLocker partition offset (default is 0)
    -p, --recovery-password[RECOVERY_PASSWORD]
                          decrypt volume using the recovery password method
    -q, --quiet           do NOT display anything
    -r, --readonly        do not allow to write on the BitLocker volume
    -u, --user-password   decrypt volume using the user password method
    -v, --verbosity       increase verbosity (CRITICAL errors are displayed by default)
    -V, --volume VOLUME   volume to get metadata and keys from

    --                    end of program options, beginning of FUSE's ones

  ARGS are any arguments you want to pass to FUSE. You need to pass at least
the mount-point.


```

I dont understand whats happening i dont know if theres smth wrong with my args eventhough i think i followed the guide correctly.
Please help me! i can answer to any question. But i need to fix my pc fast because i have important files which i need to work with

---

### Post by Mark Phelps on 2014-06-17
First of all, you've listed the volume parm twice.

Second, sdb is a disk, not a volume -- a volume is usually a partition on a disk.

---

### Post by 0pt1cKill3r on 2014-06-17
So i should replace sdb with sdb1? And i dont understand what you mean by listing the volume parm twice :/ . Can you tell me what to change?

---

### Post by Mark Phelps on 2014-06-17
I can't tell you which partition -- but if there is only one on the device, then it would be "sdb1".

As to volume, there is a Volume parameter "-V <volume>", which you already entered as "-V /media/sdb" and then you entered is a second time at the end as "--/media/windows". The "-V" parameter is sufficient. Plus, "/media/windows" is a Mount point.

And,  please do NOT PM me with questions.

---

### Post by 0pt1cKill3r on 2014-06-17
I was following this guide ([http://earthwithsun.com/questions/376533/how-to-access-bitlocker-encrypted-drive-in-linux](http://earthwithsun.com/questions/376533/how-to-access-bitlocker-encrypted-drive-in-linux))  and it tells to create  a folder /media/windows and /media/mount. (step 8) and than uses it at step 17. Thats why i used it that way. (eventhough i dont understand why). 

(p.s.: sorry i PM-ed you but was in a hurry)

---

### Post by Mark Phelps on 2014-06-17
OK, but notice at least two differences in their example:
1) they have "sdb1" for the -V parameter, not "sdb"
2) they have a space between "--" and "/media/windows", it does not look like you have one (it's hard to tell from the post).

---

### Post by 0pt1cKill3r on 2014-06-17
Thanks a lot Mark. Driver unlocked.

---

### Post by Mark Phelps on 2014-06-18
Good to hear you got it sorted!

---

