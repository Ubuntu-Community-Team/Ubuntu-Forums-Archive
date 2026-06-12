---
title: "Adobe Flash Lock-up problem"
date: 2014-01-30
forum: General Help
---

### Post by jjclonker on 2014-01-30
Ok. I started getting an annoying pop-up that said something about adobe flash not updating or installing properly so I foolishly purged adobe flash from my computer and now when I run DVDs with VLC player it plays sound, but no visual. When I tried to put it back on using software center it would get to applying changes and just lock-up applying changes forever and ever never moving an inch.

---

### Post by Bashing-om on 2014-01-30
jjclonker; Wehheell.

When at 1st you do not succeed, fire up a terminal and see what the package manager thinks of the situation as a whole.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get purge flashplugin-installer
sudo apt-get install flashplugin-installer

```
If there are errors reported, post the outputs, and we will see what there is to do !

[INDENT][INDENT]maybe yes.
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jjclonker on 2014-01-30
Everything, but the pop-up thing was solved when I restarted my computer. Your instructions hopefully solved the pop-up problem, because after I  ran the sudo apt-get purge flashplugin-installer
command it found  more flash files. So I think it is SOLVED, but I will test to see if the  pop-up is gone before I mark it SOLVED. :D

Thanks again Bashing. ;)

---

### Post by jjclonker on 2014-01-30
Pop-ups gone, adobe flash gone, video fully functional, and all applications running great!! SOLVED!!!

---

### Post by Bashing-om on 2014-01-30
jjclonker; Hey, Great !

Got out of that one lightly !

[INDENT][INDENT][INDENT]wheeewwhhh
[/INDENT][/INDENT][/INDENT]

---

### Post by jjclonker on 2014-02-01
Oh no!! I spoke to soon this pop-up is still alive:

  ```
Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.
```

---

### Post by tgalati4 on 2014-02-01
Post the output of:

```
apt-cache search flashplugin
```

It might look like:

tgalati4@Mint14-Extensa ~ $ apt-cache search flashplugin
mint-flashplugin - Metapackage for Adobe Flash plugin
mint-flashplugin-11 - Adobe Flash plugin 11
mint-flashplugin-10.2 - Adobe Flash plugin 10.2
mint-flashplugin-10.3 - Adobe Flash plugin 10.3 Beta 2
flashplugin-installer - Adobe Flash Player plugin installer
flashplugin-downloader - Adobe Flash Player plugin installer (transitional package)
flashplugin-nonfree-extrasound - Adobe Flash Player platform support library for Esound and OSS
adobe-flashplugin - Adobe Flash Player plugin version 11

It's possible that it was once provided my the mediaubuntu repository which shut down.  You might need to find an alternate source for it.

---

### Post by Bashing-om on 2014-02-01
jjclonker; Hi !

See tgalati4's last . Great point.

also I would be interested in seeing what is presently installed on the system from the PM's point of view:
```

dpkg -l flashplugin-installer

```
Conflicts ?

[INDENT][INDENT]when in doubt,
[INDENT][INDENT]ask the package manager
[/INDENT][/INDENT][/INDENT][/INDENT]

---

