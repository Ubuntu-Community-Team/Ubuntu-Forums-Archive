---
title: "[SOLVED] Torrent Software"
date: 2008-02-09
forum: General Help
---

### Post by mistweaver4 on 2008-02-09
Hey all,

im new to ubuntu and still trying to learn all the terminology so please bare with me.

ive installed Azureus on my system and that seemed to have gone fine. but when i open the program, the flash screen pops up and the program opens for about 2 seconds then closes.

i cant figure this one out. any advice is greatly appreciated!

thanks in advance!

---

### Post by randy78 on 2008-02-09
You might need to install Java or update your Java install...

BTW, you should really give Deluge a shot... it's very lightweight, supports blocklists and is very reliable.

sudo apt-get install deluge

Check out: [http://www.psychocats.net/ubuntu/java]("http://www.psychocats.net/ubuntu/java")

---

### Post by TidusBlade on 2008-02-09
I wouldn't suggest Azureus, especially if your system is not high-end, since it takes up so much RAM, and that shouldn't happen with torrent clients. I would recommend Deluge if your on GNOME, and randy78 says how to install it. Ktorrent is great for KDE, well it works better in KDE anyways, install it with "sudo apt-get install ktorrent" 
And you can use rtorrent if your like the terminal ;)

---

### Post by mistweaver4 on 2008-02-09
i tried installing deluge and i get a message in the details section with a ton of code i dont understand and a message saying the package does not contain the J2SDK documentation and that i need to download it, but i cant seem to find it at the give site. 

[http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

when i click on the file i think its looking for, it just brings me to a document, no file to download...

---

### Post by randy78 on 2008-02-09
Please post the message with the code!:popcorn:

---

### Post by Dev'olution on 2008-02-09
I've found ktorrent to be reliable also.

---

### Post by mistweaver4 on 2008-02-09
here is a really stupid question,

im not used to linux yet, only windows,
how do i copy the text from the installer window?

---

### Post by Dev'olution on 2008-02-09
> **mistweaver4 said:**
> here is a really stupid question,

im not used to linux yet, only windows,
how do i copy the text from the installer window?
If its in a terminal

> Ctrl+Shift+C

---

### Post by NightwishFan on 2008-02-09
A gui method of installing Deluge (which is what I use by the way), is to open System/Administration/Synaptic Package Manager. Type your password and search deluge. Right click it and hit mark. Then hit apply and wait. Deluge should be installed.

---

### Post by randy78 on 2008-02-09
> **mistweaver4 said:**
> here is a really stupid question,

im not used to linux yet, only windows,
how do i copy the text from the installer window?

The only stupid question is the one you don't ask!

Don't get discouraged... you will learn all you need to know if you keep trying ;)

---

### Post by mistweaver4 on 2008-02-09
that wont work...

---

### Post by randy78 on 2008-02-09
> **NightwishFan said:**
> A gui method of installing Deluge (which is what I use by the way), is to open System/Administration/Synaptic Package Manager. Type your password and search deluge. Right click it and hit mark. Then hit apply and wait. Deluge should be installed.

Ya know, it's almost starting to sound like she doesn't have all the repo's enabled, because when she tries to install it, it should automatically locate and install the dependencies for it as well...

We shall see :)

---

### Post by mistweaver4 on 2008-02-09
i did it following the GUI method. 

i dont know coding yet.

but i get an error message in the details section of the install, but i cant figure out how to copy it.

---

### Post by randy78 on 2008-02-09
I just read on Ubuntuguide.org that a lot of people have problems with the Deluge version that's in the repo's, so go here and select Ubuntu and download the proper package for your distribution (ie. Gutsy Gibbon 386 for normal machines, or the 64 bit version for 64 bit machines) after that, just double click on the file when it downloads and install it.

[http://deluge-torrent.org/downloads.php]("http://deluge-torrent.org/downloads.php")

Let me know how it works out for you ;)

---

### Post by sloggerkhan on 2008-02-09
First of all, if you want to install deluge, get it from [http://deluge-torrent.org](http://deluge-torrent.org) .
The repo version has problems and is hopelessly out of date.

2nd, probably the best client in the repos by default in terms of functioning and being gtk/gnome oriented, is transmission. The version is older, but it works fine. sudo aptitude install transmission.

I've never had anything but trouble with azureus so can't recommend it.

---

### Post by randy78 on 2008-02-09
> **sloggerkhan said:**
> First of all, if you want to install deluge, get it from [http://deluge-torrent.org](http://deluge-torrent.org) .
The repo version has problems and is hopelessly out of date.

2nd, probably the best client in the repos by default in terms of functioning and being gtk/gnome oriented, is transmission. The version is older, but it works fine. sudo aptitude install transmission.

I've never had anything but trouble with azureus so can't recommend it.

Transmission is great, and I personally use Azureus and Deluge, mainly Azureus because I can configure EVERYTHING to meet my person specifications.

It is very resource hungry though.

Honestly, with all the choices, why not try them all to see which one suits you best!?

---

### Post by mistweaver4 on 2008-02-09
okie dokie, azureus has been officially given up on

i tried deluge and it seems to be working fine.

ive downloaded the recomended newer version, but i think ill keep using this one till i run into issues. mainly because im not 100% confident that i can remove the old one without messing something new up.

thanks for all of your help!

---

### Post by sloggerkhan on 2008-02-09
If you install the .deb version from the deluge site, it's a package for the same program so the upgrade process is automatic and the previous pref files will be retained.

---

### Post by randy78 on 2008-02-09
Don't forget to mark your post as SOLVED by using the THREAD TOOLS  ;)

---

### Post by Ghuloomo on 2008-02-09
Ok, so seems azureus is not recommended by everyone. 

I'm downloading Deluge (from their website), and Transmission from the terminal. I'll see which one is better..

Btw, there is already this BitTorrent program in Applications -> Internet.. What's wrong with that?!

---

### Post by sloggerkhan on 2008-02-09
the default client doesn't really have any features. It pretty much is a GUI for a 1 torrent at a time download.

---

### Post by Ghuloomo on 2008-02-11
Aha.. I downloaded one torrent movie bin file (Meet the Spartans) through it and everything was fine, except that the speed was so slow (10KB/s). I have put Deluge and Transmission now.

---

### Post by splendid on 2008-02-14
I was able to use bit torrent (Dime a Dozen) site yesterday.  Went to continue a download by clicking on the Torrent and it appears like it is doing something, and then nothing happens.  

Tried re-booting, using a different torrent, and the same thing happens.

Any ideas???

Splendid:guitar:

---

### Post by cox377 on 2008-02-24
Just installed Deluge after seeing these posts.. have gone right off the new azureus fuse... really impressed with such a lite client!!

CoXen

---

