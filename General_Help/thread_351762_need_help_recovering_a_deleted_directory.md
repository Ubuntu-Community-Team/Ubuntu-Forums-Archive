---
title: "need help recovering a deleted directory"
date: 2007-02-02
forum: General Help
---

### Post by donut_irl on 2007-02-02
Hi,

Something really weird just happened
I was looking through some files using a terminal
and typed cd.. instead of cd ..
and now the directory is gone!

This is from the terminal:
:/share/video/backup/dvd/video_ts$ du -h
65M     .
:/share/video/backup/dvd/video_ts$ cd ..
:/share/video/backup/dvd$ du -h

65M     ./video_ts
32K     ./audio_ts
65M     .
:/share/video/backup/dvd$ cd ..
:/share/video/backup$ cd..
bash: cd..: command not found
:/share/video/backup$ cd ..
cd: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
:/share/video/grey1/..$ cd ~
:~$ cd /share/video
bash: cd: /share/video: No such file or directory


/share is the mount point for a 28GB partition of my harddisk i use to share files between XP and Ubuntu ... i haven't booted XP in a week (fortunately :) )

also here's a before and after using df

:/share/video/backup/dvd/video_ts$ df
...............
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6             28395904  13952544  14443360  50% /share
...............

:/share$ df -h
Filesystem            Size  Used Avail Use% Mounted on
..............
/dev/hda6              28G  7.6G   20G  28% /share
................

so .. /share/video which used to have ~7GB in it has now been removed ..
all i did was type cd.. instead of cd .. ... i do this all the time ... was it just my 100,000,000th time?
df says that i've gone from ~13GB free space to 20GB free space .. meaning the directory is gone :(

any ideas how to recover?

---

### Post by Topsiho on 2007-02-02
I don't think I can tell you what happened.

I tried using cd.. in a directory which I don't mind to loose, but I did not loose it:

jaap@Bromo:~$ ls
100HP318            Desktop    Foto's                     iso             kubuntugids  pdf       tulip_netwerkkaartdrivers
Barricade           doc        fstab_en_andere_bromo.odt  jpg             lijst.vcf    png
belastingdienst.nl  downloads  gif                        kmail_inbox     Linuxtutor   Qbasic
book                exe        Grokking-the-GIMP-v1.0     kmail_sentmail  Mail-suse    rute
cartoons            Filmpjes   grub.img                   KOrganizer      manuals      tarball
cpp                 Fotomap    Huiskozijnen               KRL             Mp3          Testdisk
jaap@Bromo:~$ cd Testdisk/
jaap@Bromo:~/Testdisk$ ls
README_testdisk.odt  testdisk-6.4.dos.zip  testdisk-6.4.linuxstatic.tar.bz2  testdisk-6.4.win.zip
jaap@Bromo:~/Testdisk$ cd..
bash: cd..: command not found
jaap@Bromo:~/Testdisk$ ls
README_testdisk.odt  testdisk-6.4.dos.zip  testdisk-6.4.linuxstatic.tar.bz2  testdisk-6.4.win.zip
jaap@Bromo:~/Testdisk$ cd ..
jaap@Bromo:~$ ls
100HP318            Desktop    Foto's                     iso             kubuntugids  pdf       tulip_netwerkkaartdrivers
Barricade           doc        fstab_en_andere_bromo.odt  jpg             lijst.vcf    png
belastingdienst.nl  downloads  gif                        kmail_inbox     Linuxtutor   Qbasic
book                exe        Grokking-the-GIMP-v1.0     kmail_sentmail  Mail-suse    rute
cartoons            Filmpjes   grub.img                   KOrganizer      manuals      tarball
cpp                 Fotomap    Huiskozijnen               KRL             Mp3          Testdisk
jaap@Bromo:~$

So it is not just using cd.. instead of cd .. which threw away your directory.

Greetz,

Topsiho

---

### Post by lamego on 2007-02-02
> and typed cd.. instead of cd ..
Just to clarify, this would never delete anything, you have just use an invalid command. Or you have deleted/moved with your data with rm/mv or you have done it with the graphical interface.
If it was deleted with rm, there is no way you can undelete it.

---

### Post by donut_irl on 2007-02-02
i figured it couldn't have been cd..

but i went no where near that directory in nautilus and definitely didn't rm or mv anything

is there any file recover procedures i can use to see if the data is still there?

thanks

---

### Post by donut_irl on 2007-02-02
oh yeah, forgot to say nothing in the trash ...

---

### Post by Topsiho on 2007-02-03
> **donut_irl said:**
> oh yeah, forgot to say nothing in the trash ...

I figured this because if it were in the trash it would still occupy disk space.

I am glad it was not cd.. as in that case we could better go back to Windows :(

Must have typed something inadvertently, but what, that is the question...

Topsiho

---

