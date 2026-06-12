---
title: "Kopete 0.11 beta 2, webcam and more !"
date: 2005-10-21
forum: General Help
---

### Post by Zinoc on 2005-10-21
Hi everybody !
I just want to signal that webcam on msn, nudges and personalized messages are now functionals in kde 3.5 beta2 packages.
I only try receiving webcam (don't have one myself...), and I haven't find the way to export my personalized message. 
That's official, now I prefer kopete to gaim. Great job guys ! Keep going !

---

### Post by stoeptegel on 2005-10-30
I also compiled kopete from SVN today. It has a nifty feature to show your 'now playing' from amarok with a script from kde-apps.org.

I like it very much. :)

---

### Post by dr.drake on 2005-11-12
hello,

it might be yet another stupid question, but how do I get this beta version. 
I upgraded KDE, but my Kopete still runs @: **Kopete 0.10.4 (Using KDE 3.5 (RC1))**

thanks, eric.

---

### Post by dr.drake on 2005-11-12
ok. I got it working using only a couple of steps:
first of all, it seems like you only need KDE 3.4 for this, but if you have to get KDE 3.5 [this thread]("http://www.ubuntuforums.org/showthread.php?t=89199&highlight=kde+3.5") will tell you how...
now to get Kopete 0.11 beta 2 (I got most of the instructions from [this site]("http://kopete.kde.org/svnaccess.php") ) you need to:

 ```
sudo apt-get install build-essential
```and set a root password to make the last command work:

```
sudo passwd root
```install **subversion** to make the **svn** command work
install **automake 1.6.1 **or higher to make the **make** command work


```
svn co -N svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kdenetwork
cd kdenetwork
svn up kopete
svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kde-common/admin
make -f Makefile.cvs
./configure --enable-debug
cd kopete
make
su -c "make install"
```

now it should be working...

eric.

---

### Post by Jeff Eklund on 2005-11-13
I got it when I upgraded to 3.5b2. It says that it's version 0.11b2 (0.10.93) but the VERSION-file in the svn-rep says the latest version is 0.10.922, and I can't seem to find any webcam support... Or at least I haven't found any button to press, to enable it. It might just be me not having noticied it. Can someone point it out for me?

---

### Post by daller on 2005-12-16
Is the one included in KDE3.5 final a beta? - Mine says "Kopete 0.11 (Under KDE 3.5.0)"

I can't send webcam-images it seems... the remote computer says: "No picture recieved from the webcam" (Translated from danish!)

---

### Post by lex on 2006-01-08
[QUOTE=dr.drake]ok. I got it working using only a couple of steps:
first of all, it seems like you only need KDE 3.4 for this, but if you have to get KDE 3.5 [this thread]("http://www.ubuntuforums.org/showthread.php?t=89199&highlight=kde+3.5") will tell you how...
now to get Kopete 0.11 beta 2 (I got most of the instructions from [this site]("http://kopete.kde.org/svnaccess.php") ) you need to:

 ```
sudo apt-get install build-essential
```and set a root password to make the last command work:

```
sudo passwd root
```install **subversion** to make the **svn** command work
install **automake 1.6.1 **or higher to make the **make** command work


```
svn co -N svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kdenetwork
cd kdenetwork
svn up kopete
svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kde-common/admin
make -f Makefile.cvs
./configure --enable-debug
cd kopete
make
su -c "make install"
```

now it should be working...

eric.[/QUOTE]


Hi can I use the new beta version in Ubuntu and how do i get it?
I tried doing the above stuff but it dosent work in ubuntu. Any help would be much appreciated.
Thanks
Lex

---

### Post by dr.drake on 2006-01-11
well, I'm not really an expert, but since you use Ubuntu, I reckon you run the Gnome (default) desktop, not the KDE? because Kopete is a program built for KDE (hence the K at the start of the name), and as far as I understand, you really need the latest version from KDE for the beta Kopete to work...

eric.

---

### Post by lex on 2006-01-11
[QUOTE=dr.drake]well, I'm not really an expert, but since you use Ubuntu, I reckon you run the Gnome (default) desktop, not the KDE? because Kopete is a program built for KDE (hence the K at the start of the name), and as far as I understand, you really need the latest version from KDE for the beta Kopete to work...

eric.[/QUOTE]

Thanks for your help.
Lex

---

