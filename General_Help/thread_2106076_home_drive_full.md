---
title: "home drive full"
date: 2013-01-18
forum: General Help
---

### Post by toeknee2120 on 2013-01-18
Over the weekend, my 1TB HD seemed to fill up to 100%. I tried troubleshooting, and after deleting some music and movies, it is still pretty full, more that what I would expect it to be.

Attached is a screenshot of my Disk Usage Analyzer, and below is what I get when I run **df-h**. My Public folder is only ~280GB, so I don't see what else is taking up so much space.
```

Filesystem                        Size  Used Avail Use% Mountedon
/dev/mapper/vol--group--a-lvroot   15G  6.3G  7.8G  45% /
udev                              5.9G  8.0K  5.9G   1% /dev
tmpfs                             2.4G  896K  2.4G   1% /run
none                              5.0M     0  5.0M   0% /run/lock
none                              5.9G  344K  5.9G   1% /run/shm
cgroup                            5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/mapper/vol--group--a-lvtmp    15G  166M   14G   2% /tmp
/dev/sda1                        1008M  106M  852M  11% /boot
/dev/mapper/vol--group--a-lvusr    15G  3.2G   11G  23% /usr
/dev/mapper/vol--group--b-lvhome  985G  898G   38G  97% /home
/dev/mapper/vol--group--a-lvvar    15G 1015M   14G   8% /var
```

---

### Post by alphaamanitin on 2013-01-18
You should look into each aspect of  your home folder and see if you can narrow down exactly where all the files are and what they are.

AlphaA

---

### Post by dannyboy79 on 2013-01-18
have you checked your trash? i think /home/username/.local/share/Trash

this command will show you the top 10 locations where the largest files are
```
du -a /home/ | sort -n -r | head -n 10
```

then when it lists the folders, do the search again but using that folder now, for example
```
du -a /home/username/.local/ | sort -n -r | head -n 10
```

your picture is indeed weird, showing /home/ being so full but no sub-folder besides public having much in it. i wouldn't trust disk usage analyzer, try the command i posted above. also, try to restart your computer

---

### Post by toeknee2120 on 2013-01-20
**alphaamanitin**, I tried everything I could to find what the problem was in my home drive.  Turns out, using the commands **dannyboy79** posted, it was my .xsession-error file. It was a couple hundred gigs! So now I have 657G available. I see others on the forums have had the same problem. 

Anyways, thanks for the help and quick responses.

---

### Post by dannyboy79 on 2013-01-20
you should have peaked at it's contents to see what error it is logging to see if you can solve the issue. otherwise it's just going to keep filling up. good luck
don't forget to mark the thread solved using the thread tools in the upper corner of the thread

---

