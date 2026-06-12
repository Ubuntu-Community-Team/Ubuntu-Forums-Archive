---
title: "[SOLVED] Help, new to linux!!!"
date: 2007-10-04
forum: General Help
---

### Post by perlluver on 2007-10-04
Unable to save bookmarks in /home/perlluver/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.

Getting this message every time I close, the home folder.  Not sure how to fix it.

---

### Post by IronArjen on 2007-10-04
If you re new to Linux mu guess is that it is a matter of permission, although I do not understand what the message about the hard disk has got to do with it. I guess your bookmarks are coming from an earlier computer format? In that case the "ownership" will correspond to your old settings and you home@perluver have no permission.

Open a terminal, go to the correct directory and change either ownership or simply the permissions using the CHMOD command. You ll find more about this and other linux commands @ 

[http://www.linuxcommand.org/lts0070.php#chmod](http://www.linuxcommand.org/lts0070.php#chmod)

I guess the page will also describe how to change ownership. You might need to do this to several directories and or files. Similar things might happen transporting addressbooks etc.

I can recommend to do the quick linux command course at the page above, will take you 1 hr and you &#314;l underrstand a lot more

---

### Post by perlluver on 2007-10-04
Unable to save bookmarks in /home/perlluver/.kde/share/apps/d3lphin/bookmarks. xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive

---

### Post by perlluver on 2007-10-04
That didn't help, it just does the same thing.  I opened the folder as root, and as soon as I close it as a regular user it does the same thing.

---

### Post by IronArjen on 2007-10-04
I am not sure I understand what you did.
Did yo try: chmod 777 bookmarks.xml?

---

### Post by por100pre1 on 2007-10-04
If you suspect the disk is full try removing the downloaded packages:

```
sudo apt-get clean
```

Lets see who owns that file:

```
cd /home/perlluver/.kde/share/apps/d3lphin
```

```
ls -al
```

post the results. :-k

---

### Post by perlluver on 2007-10-04
total 16
drwx------  2 perlluver perlluver 4096 2007-10-04 13:41 .
drwxr-xr-x 37 perlluver perlluver 4096 2007-10-03 20:22 ..
-rw-r--r--  1 root      root      1132 2007-10-04 13:41 bookmarks.xml
-rw-r--r--  1 root      root      1132 2007-10-04 13:41 bookmarks.xml.bak

---

### Post by perlluver on 2007-10-04
Thank you!!!  I tried 700 but it didn't work, 777 did work.  Thank you very much for your help.

---

### Post by por100pre1 on 2007-10-04
It should be yours, not root's:

```
sudo su -c 'chown -R perlluver:perlluver /home/perlluver/.kde'
```

---

### Post by IronArjen on 2007-10-04
Then indeed it was due to the fact that your file is owned by another "name" coming from you old computer or former OS

Be careful with 777 since you allow all to all. If I were you I would is change ownership.

sudo chown perlluver bookmarks.xml 

or of course

sudo chown perlluver *.*

---

### Post by joao82 on 2007-10-28
I don't know why, but the same started happening to me 5 minutes ago and this fixed.
thanks.

---

