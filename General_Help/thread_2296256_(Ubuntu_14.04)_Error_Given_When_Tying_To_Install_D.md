---
title: "(Ubuntu 14.04) Error Given When Tying To Install Deluge"
date: 2015-09-24
forum: General Help
---

### Post by jooge on 2015-09-24
I am trying to install Deluge bittorrent client. I have tried installing it via PPA & 

I seem to be getting this error both times:
```

The following packages have unmet dependencies:
deluge : Depends: python-libtorrent (>= 0.14.9) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

How can I fix this issue?

---

### Post by ian-weisser on 2015-09-24
Why are you using a PPA?
Have you tried the fine version already in the Ubuntu repositories?
Are you following instructions from someplace? If so, please show us a link.
What version of Ubuntu are you running? 12.04? 14.04? 15.04?

---

### Post by corneliuss2 on 2015-09-24
**python-libtorrent** is in Ubuntu repos (**universe**) and its version is **0.16.18-1**.

I suggest you do:

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get install python-libtorrent deluge
```

---

### Post by v3.xx on 2015-09-24
> **ian-weisser said:**
> Why are you using a PPA?
Have you tried the fine version already in the Ubuntu repositories?
Are you following instructions from someplace? If so, please show us a link.
What version of Ubuntu are you running? 12.04? 14.04? 15.04?
Yes ^^

Remove the ppa

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9)

And install from the ubuntu sources.
```
sudo apt-get install deluge
```

---

### Post by monkeybrain20122 on 2015-09-24
Which Ubuntu release is that? Which deluge ppa?  Seems that 0.14.9 is really old.

Edited: Oops, between I pressed the save button and the message got posted a whole bunch of people's posts have showed up. UF sometimes takes a long time..

---

### Post by jooge on 2015-09-24
I'm running 14.04.

The Deluge from the Ubuntu software center is old.

Here is where I got the PPA from: [http://dev.deluge-torrent.org/wiki/Installing/Linux/Ubuntu#AddDelugePPARepository](http://dev.deluge-torrent.org/wiki/Installing/Linux/Ubuntu#AddDelugePPARepository) I was just trying to install the latest version.

> **corneliuss2 said:**
> **python-libtorrent** is in Ubuntu repos (**universe**) and its version is **0.16.18-1**.

I suggest you do:

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get install python-libtorrent deluge
```

This did not work for me but thanks Corni.

This may sound like a rather nooby question but how do I delete the PPA? I found them in folder /etc/apt/sources.list.d but now what do I do?

> **v3.xx said:**
> Yes ^^

Remove the ppa
[URL="http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9"]http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9
[/URL]
And install from the ubuntu sources.
```
sudo apt-get install deluge
```

I get this error when I try to dl it from the Ubuntu sourses:

[[IMG]http://i.imgbox.com/o9ozTd19.png[/IMG]](http://imgbox.com/o9ozTd19)

---

### Post by v3.xx on 2015-09-24
> This may sound like a rather nooby question but how do I delete the PPA
Link in my first post.

Did you download the right ppa?  Does it say trusty in your sources list?

---

### Post by v3.xx on 2015-09-24
> I get this error when I try to dl it from the Ubuntu sourses:
You must first remove the ppa.

---

### Post by jooge on 2015-09-24
Yes v3.xx its trusty.

I just removed the PPA

---

### Post by jooge on 2015-09-24
Got It Finally!!! thank you all that helped. I really appreciate your time and effort. Have a great day/evening/night (Whichever applies to you) :P

---

