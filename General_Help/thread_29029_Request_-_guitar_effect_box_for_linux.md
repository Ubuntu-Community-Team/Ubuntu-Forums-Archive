---
title: "Request - guitar effect box for linux"
date: 2005-04-22
forum: General Help
---

### Post by invchrist on 2005-04-22
Anyone used any guitar fx box-utilities with ubuntu?

In the repositories (with apt-cache search) I can't find GNUitar, GTKgep, stompboxes or ViaGratt which could qualify as good linux guitar-effects tools.

Anyone had any success with installing these or knows other tools?

PS: i'm still running warty

EDIT: sorry moderators, could someone move this to warty-other applications

---

### Post by invchrist on 2005-04-22
In the meantime I figured out the way to compile GNUitar ([www.gnuitar.com](www.gnuitar.com)) from source with warty, so i'll post it for future reference...

You need to do the following as a preparation before the build:

```
sudo apt-get install build-essential
sudo apt-get install libglib-1.2dev
sudo apt-get install libgtk-1.2dev
```
Or (alternatively) use synaptic to install build-essential, libglib-1.2dev and libgtk-1.2dev

Now we are getting the file and a patch (you can't compile without it):

```

sudo wget http://belnet.dl.sourceforge.net/sourceforge/gnuitar/gnuitar-0.3.1.tar.gz
sudo tar -xzf gnuitar-0.3.1.tar.gz
sudo wget http://www.gnuitar.com/downloads/patches/patch-0.3.1-1
sudo patch -d gnuitar-0.3.1 -p1 <patch0.3.1-1
```
Always check the output of the console to see if things are going right!

Now configure, make and make install:

```
cd gnuitar-0.3.1
sudo ./configure
sudo ./make
sudo ./make install
```
So, if everything went well , you can now start GNUitar with:

```
gnuitar
```
All comments welcome, enjoy !

---

### Post by Jaymoid on 2006-03-18
Hi, 

Thanks for the how to, it was pretty good (although the dashes should come after the version number on glib and gtk).

I have also used Tapiir, and ecamegapedal which are both in apt. I still cant get stomboxes installed though, I get errors during the make : ( if you get it working please post your methods.

I have also tried creox too, but this installs, loads but doesnt seem to want to do anything. 

I am also after some kind of amp model program so that you can select classic amps and preset your own, e.g. marshall jcm's, vox ac30's etc. 

I also found this article, might be worth a read!
[http://www.linuxdevcenter.com/pub/a/linux/2001/07/20/linux_guitar.html?page=4](http://www.linuxdevcenter.com/pub/a/linux/2001/07/20/linux_guitar.html?page=4)
Also 
[http://ubuntustudio.com/wiki/index.php/Welcome%2C_Musicians%21](http://ubuntustudio.com/wiki/index.php/Welcome%2C_Musicians%21)

Thanks again
James

---

