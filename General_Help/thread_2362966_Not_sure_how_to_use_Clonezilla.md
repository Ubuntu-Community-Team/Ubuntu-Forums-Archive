---
title: "Not sure how to use Clonezilla"
date: 2017-06-04
forum: General Help
---

### Post by raleigh3 on 2017-06-04
I want to clone sda and store the image on sdb2.
  
However, when it asks "Which directory is for Clonezilla image." there is no pick for sdb2.

  
Sdb2 is mounted.

---

### Post by ajgreeny on 2017-06-04
You will probably need to use the mountpoint rather than try an sdx# naming system, so possibly it will be something like /media/username/diskname.

---

### Post by monkeybrain20122 on 2017-06-04
Fsarchiver is much more flexible than Clonzilla and your use case is trivial, you can even do it while using your system (live image)

Say you are in /dev/sda1, which you want to clone, mount /dev/sdb2

then just run the savefs command with the options -a and -A (sudo fsarchiver -a -A -v savefs  ..., first command in the quickstart) [http://www.fsarchiver.org/quickstart/](http://www.fsarchiver.org/quickstart/) The -a and  -A options are for live cloning. i.e you can use the system while cloning it, just don't alter it by installing or updating software.

fsarchiver is in the repo.

There is also a gui if you are so inclined. It is very easy to use but less flexible (you can't exclude directories as far as I know) and you need to compile it from source (which is quite easy if you have qt installed)  [https://sourceforge.net/projects/qt4-fsarchiver/](https://sourceforge.net/projects/qt4-fsarchiver/) 

Edited:There is actually a ppa so no compiling is necessary [https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver-64-bit](https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver-64-bit)

---

### Post by raleigh3 on 2017-06-04
Thanks.

I used this to backup.

```
sudo fsarchiver -j4 savefs -a -A /media/andy/MAXTOR_SDB2/Fs_Archiver_Backups/6_4_17_Backup.fsa /dev/sda1
```

Would this work to restore it ?

```
[FONT=Courier 10 Pitch][SIZE=4]sudo [/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4]fsarchiver -[/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4]j4[/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4] restfs [/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4]/media/andy/MAXTOR_SDB2/Fs_Archiver_Backups/6_4_17_Backup.fsa[/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4] id=0,dest=/dev/sda1[/SIZE][/FONT]
```

---

### Post by monkeybrain20122 on 2017-06-04
> **raleigh3 said:**
> 


Would this work to restore it ?

```
[FONT=Courier 10 Pitch][SIZE=4]sudo [/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4]fsarchiver -[/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4]j4[/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4] restfs [/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4]/media/andy/MAXTOR_SDB2/Fs_Archiver_Backups/6_4_17_Backup.fsa[/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=4] id=0,dest=/dev/sda1[/SIZE][/FONT]
```


yes, and actually you can restore it anywhere providing the partition is big enough for the data cloned, which is not like clonezilla for which the target has to be as least as big as the original partition even if the original partition is mostly empty. So if you have say a spared hard drive laying around you can actually test your backup by restoring to it (change dest accordingly) Of course to restore to /dev/sda1 you need to run fsarchiver from somewhere else, e.g a ubuntu live usb with fsarchiver installed.

---

### Post by raleigh3 on 2017-06-05
Thanks a lot.

---

