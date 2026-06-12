---
title: "Can't install Firefox 2 in Edgy"
date: 2006-11-07
forum: General Help
---

### Post by geetarista on 2006-11-07
I really need some help getting Firefox to work in Edgy.  I've been trying to figure this out by searching and toying for hours and still can't get it... ](*,) 

I upgraded to Edgy from Dapper without any problems, except that Firefox was still the old version--probably because I installed it manually or through Automatix (can't remember which one.  After trying for a while, I just deleted anything and everything that had to do with Firefox and now I can't re-install it.  When I try to install, I get this error:

```
(Reading database ... 238313 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0+0dfsg-0ubuntu3_i386.deb) ...
Replaced by files in installed package libnss3 ...
dpkg: error processing /var/cache/apt/archives/firefox_2.0+0dfsg-0ubuntu3_i386.deb (--unpack):
 unable to create `./usr/lib/firefox/firefox': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0+0dfsg-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

For some reason, when I do # sudo aptitude install firefox, it tries to install gnome-app-install as well, but it still doesn't work.  I don't want to install it manually again because I don't want any future problems, especially when upgrading.

Any ideas?

---

### Post by Zalbor on 2006-11-07
This line seems to me to be the problem:
```
 unable to create `./usr/lib/firefox/firefox': No such file or directory
```
It seems to be the . in the beginning; it's trying to make this directory starting from where you are instead from / (the root). How are you trying to install it?

---

### Post by Vashu on 2006-11-07
Is your ubuntu-desktop/kubuntu-desktop/xubuntu-desktop package broken? If it is you can just use synaptic to repair the broken dependencies ralated to FF or maybe just re-install it.

seems odd you get that error thou. sudo should fix that.

---

### Post by taurus on 2006-11-07
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by geetarista on 2006-11-07
@ Zalbor: I'm just doing this:

sudo apt-get install firefox

I get the same error if I try aptitude as well.  I even removed the package and tried to re-install it again.

@ Vashu: I re-installed ubuntu-desktop, but that didn't really help anything.

@ taurus: > I don't want to install it manually again because I don't want any future problems, especially when upgrading.

---

### Post by geetarista on 2006-11-07
When trying to fix packages using Synaptic, this is the error I get:

```
E: /var/cache/apt/archives/firefox_2.0+0dfsg-0ubuntu3_i386.deb: trying to 
overwrite `/usr/lib/mozilla-firefox', which is also in package j2re1.4
```

The thing is, there is no mozilla-firefox folder in /usr/lib.  And I don't know what j2re has anything to do with this...

What's going on?!

---

### Post by taurus on 2006-11-07
```
/usr/lib/firefox
```

---

### Post by geetarista on 2006-11-07
```
/usr/lib/firefox
```

Doesn't exist.  Maybe you would like to elaborate...  :)

---

### Post by geetarista on 2006-11-10
Anyone else have any ideas?

---

### Post by geetarista on 2006-11-12
Can someone *please* help me?  I can't even install or pretty much do anything with packages because of this problem...

---

### Post by bollix47 on 2006-11-12
Basically, I think your file system has been messed up and short of re-installing edgy I'm not sure you can solve this.  If your home is on a separate partition then re-installing edgy would probably be your best bet.

Having said that here are a few commands you could try:

```
sudo mkdir /usr/lib/mozilla-firefox
sudo mkdir /usr/lib/firefox
sudo apt-get install mozilla-firefox
sudo apt-get install firefox
```


You must have the universe repository checked to get the mozilla-firefox installed.
Easiest way to do this is open synpatic and click on settings - repositories, and put a checkmark beside the line ending with "universe".
Then click on the reload button in synaptic.

Try that and get back to us with any errors.

---

### Post by geetarista on 2006-11-12
Hey thanks so much bollix!!  All I had to do was:

```
sudo mkdir /usr/lib/mozilla-firefox
sudo apt-get install firefox
```

And it worked!!!  Don't know why I didn't think of that before...  :-D

Thanks again!

---

