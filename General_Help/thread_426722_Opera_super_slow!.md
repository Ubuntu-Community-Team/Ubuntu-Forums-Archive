---
title: "Opera super slow?!"
date: 2007-04-28
forum: General Help
---

### Post by herbster on 2007-04-28
I had upgraded to opera 9.20 from 9.10 last week and ever since it is going incredibly slow with more than 2 or 3 tabs open. I have removed it, reinstalled it and the same thing. And when I reinstall it via .deb, after it's installed it keeps saying (paraphrased):

```
Error: conflicts with package opera
```

But I have removed the doggone thing! I have no special effects in the Appearance, standard skin and it was running just fine before.

How do I COMPLETELY remove/clean this thing out (I mean ENTIRELY)??? Maybe then reinstall and it will be okay?

Also, I couldn't find 9.10 on the opera site, as I thought maybe reverting to that version would fix it...

Any help appreciated!!!

---

### Post by orlox on 2007-04-28
If there's anything of opera left on your system, I believe this should obliterate it:

> dpkg --purge opera

---

### Post by herbster on 2007-04-29
orlox,

I just did that, and I even removed my /home/usr/.opera, even rebooted, then I installed the opera9.20.deb again and when it was done installed it said "Error: Conflicts with installed package Opera" again!! And it's still slow as hell.

Any ideas?! This is bogglin' me mind!

---

### Post by finferflu on 2007-04-29
I don't think slowness depends from that message. I've been having that message since the Dapper times, and Opera has always worked fine. Maybe there's a problem with the qt/gtk libraries. Have you got by any chance KDE or any gtk-qt-engine installed? That's what usually slows everything down...

---

### Post by Nameeater on 2007-05-02
I am also having this exact same problem, I do not have any qt libraries other than the standard ones.

I believe this happened when they had to patch Opera because it stopped working with one of the feisty X libraries, I could be wrong, but ever since that upgrade I've had a laggy Opera with more than 8~ Tabs open which is lame, as I can have up to 15-20 open.

---

### Post by kerry_s on 2007-05-02
maybe try the regular debian opera->

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free 

The key if you want to keep the repo->

sudo gpg --keyserver subkeys.pgp.net --recv-key 033431536A423791
sudo gpg --armor --export 033431536A423791| sudo apt-key add -

---

### Post by herbster on 2007-05-02
finferflu,

How do I find out if I have a gtk-qt-engine installed?

Nameeater,

I am using Edgy, and it's sluggish as all get out.

---

### Post by finferflu on 2007-05-03
> **herbster said:**
> finferflu,

How do I find out if I have a gtk-qt-engine installed?

Usually they're there if you have Kubuntu installed, and could be there if you played too much with KDE apps...

---

### Post by zvacet on 2007-05-03
Download deb file from [http://www.opera.com/download/]("http://www.opera.com/download/")

Don´t worry about error massage.You will get this massage every time when you try to install newer version then one that is in repos.Double click on downloaded file and you will see that dependecies are installed first.

---

### Post by eldarion on 2007-05-04
I had the same problem when updated opera from 9.10 to 9.20. Just Remove your ~/.opera directory and start opera again. 

If you whant to preserve your bookmarks, notes, search engines and last opened windows make a backup of this files from your ~/.opera directory first:

- search.ini
- notes.adr
- opera6.adr
- sessions/autosave.win

then remove all files and folders from the ~/.opera directory, copy those files to that directory again and start opera.

At least it works on my ArchLinux machine.

---

### Post by Useff on 2007-05-06
> **eldarion said:**
> I had the same problem when updated opera from 9.10 to 9.20. Just Remove your ~/.opera directory and start opera again. 

If you whant to preserve your bookmarks, notes, search engines and last opened windows make a backup of this files from your ~/.opera directory first:

- search.ini
- notes.adr
- opera6.adr
- sessions/autosave.win

then remove all files and folders from the ~/.opera directory, copy those files to that directory again and start opera.

At least it works on my ArchLinux machine.


This worked for me. Thanks.

---

### Post by asipi on 2007-05-08
herbster is opera quicker now with the debian package?
I have strange experiments with ubuntu deb 9.2... if a page consists a flash objects and I start to switching among the tabs, opera getting slower and slower. I checked, and plugin libflashplayer.so eated up cpu, but if I do not touch the mouse for a while cpu level decreased, but when I started to switch again between tabs, same things happen, and nothing change if I close all the tabs with flash object :( dunno if opera bug or the ubuntu package of opera causes this

---

### Post by serine on 2007-06-04
I too have a problem with opera. whenever i use flash plugin it starts to use 100% when changing tabs and works dreadfully slow ... on the other side, firefox is just as fast with flash, java, and everything like opera without them. i've tried to delete my config files and it didnt help. opera often starts to work badly even if i dont use flash... i dont have an idea what to do. is it a problem with QT ?

---

### Post by pak33m on 2007-06-04
herbster,

Firstly you need to remove and purge Opera.  You would type the following (at the CLI):

sudo apt-get --purge remove opera

This will remove Opera and the Opera configuration files that you are manually removing.

Then you should reinstall Opera from a few methods:

1.  [http://www.opera.com/download/](http://www.opera.com/download/) and manually install the .deb file by typing the following (at the CLI):

sudo dpkg -i opera<package>.deb

2.  Add deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main to your sources.list and install through apt-get by typing the following (at the CLI):

sudo apt-get update
sudo apt-get install opera

If you get an error here about failed dependencies type the following (at the CLI):

sudo apt-get -f install

Then Opera will be installed just after that.

I install weeklies of Opera  from [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) but I use the shared version (or opera_<date>.6-shared-qt_en_i386.deb ) unlike the static version offered in the aforementioned 2 method.  The weeklies are in development versions.  I have not had very many problems using the shared versions but I have with the static.

I hope this helps you or anybody.

---

