---
title: "Linux Daa Format Manager-Extractor"
date: 2006-07-06
forum: General Help
---

### Post by nudnik on 2006-07-06
Is there something in the repositories, or something I can download elsewhere that will allow me to extract files from "daa" images (Power ISO format, a Windows program)? I would prefer a pure Linux application if possible, in order to avoid using Wine etc.  

:confused:

---

### Post by magomago on 2006-07-13
I too would like to know!

---

### Post by TKM625 on 2006-07-20
Anybody know the answer to this? I am also in need of a program to burn a daa file, or at least convert it to something else I can use.

---

### Post by srinig on 2006-08-02
I am also in need of a program that would mount/burn daa files, but unfortunately, [http://en.wikipedia.org/wiki/Direct_Access_Archive](http://en.wikipedia.org/wiki/Direct_Access_Archive) says that "DAA, is a proprietary file format for disk image files" :rolleyes:  , and also, "PowerISO ([http://www.poweriso.com/](http://www.poweriso.com/)) is the only application used to create and mount DAA disk images". :-k

---

### Post by airtonix on 2006-11-11
and if you look a bit further into the text, you'll narrow your eyes in realisation of their crafty neglegence of linux.,..

in other words further down the page is a download link for a linux command line tool

---

### Post by movil on 2006-12-02
Yeah, airtonix is completely focused.

[http://www.poweriso.com/download.htm](http://www.poweriso.com/download.htm)

Now look what I'm extracting it looks like if I'm gonna have a lot of fun:

> 
[email]syl@nel:~/torrent/QUAKE.4.DVD[/email]$ poweriso convert /home/syl/torrent/QUAKE.4.DVD/quake4.daa -o /home/syl/torrent/quake.iso -ot iso

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

Converting from /home/syl/torrent/QUAKE.4/quake4.daa to /home/syl/torrent/quake.iso ...    51%


---

### Post by Kelderkeuken on 2006-12-07
```
wget http://poweriso.com/poweriso.tar.gz
tar -zxvf poweriso.tar.gz
mv poweriso /usr/bin
rm poweriso.tar.gz

poweriso -?
```

---

### Post by pilot550 on 2007-04-15
PowerISO for linux drove me crazy. I finally got the command lines down when I tried to open a .daa file it said was too large. Yea, too large unless I pony up $29.95 to register the program. Then I found AcetoneISO. No size limitations, nice graphical interface, you can mount, extract, convert files. Oh, and it's free. Make sure you install Kommander from the repo's before you install the Deb. Check it out for yourself. It's perfect for a linux noob like me.

[http://kde-apps.org/content/show.php?content=44805]("http://kde-apps.org/content/show.php?content=44805")
:KS :KS :KS :KS :KS

---

### Post by akba0012 on 2007-09-17
> **pilot550 said:**
> PowerISO for linux drove me crazy. I finally got the command lines down when I tried to open a .daa file it said was too large. Yea, too large unless I pony up $29.95 to register the program. Then I found AcetoneISO. No size limitations, nice graphical interface, you can mount, extract, convert files. Oh, and it's free. Make sure you install Kommander from the repo's before you install the Deb. Check it out for yourself. It's perfect for a linux noob like me.

[http://kde-apps.org/content/show.php?content=44805]("http://kde-apps.org/content/show.php?content=44805")
:KS :KS :KS :KS :KS

After i download and open it, it The package installer says "error: cannot install 'konqueror".... what does that mean? How do i install this thing?

---

### Post by wishes on 2007-10-02
poweriso worked fine out of the box for me. No apparent size restriction (however i was decompressing 1.5gb)

Thanks! the .daa files drive me nuts too :/

---

### Post by RRS on 2007-10-14
Poweriso worked fine for me too. Again, files less then 700MB's though. 

Also, I'm using Gutsy.

Just did a copy/paste from Kelderkeuken's post, thanks :)

---

### Post by bulletxt on 2007-10-15
just a quick note:
AcetoneISO is a KDE software and requires konqueror and konsole to be installed.
it seems svn version is getting better about this.

sudo apt-get install konqueror konsole

---

