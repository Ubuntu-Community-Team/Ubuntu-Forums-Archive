---
title: "How to resume broken ISO download - help needed"
date: 2008-05-09
forum: General Help
---

### Post by gs_berg on 2008-05-09
In Ubuntu 7.10, I had tried to download Knoppix, but the download was broken I was left with two files: KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso (0 B) and KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso.part (3.1 GB).  The complete file is one more gig.  I already used up much of my bandwidth, so I saved these files on a DVD.

Is there any simple way to complete this download in Ubuntu 8.04 or Kubuntu 7.10.  I remember that I could resume such downloads easily in Fedora Core 6, but I erased Fedora.

Thanks for your help.

---

### Post by skymera on 2008-05-09
In Windows, Yes there is a way to resume downloads.
I use it for big files

[http://www.freedownloadmanager.org/](http://www.freedownloadmanager.org/)

You can stop, pause and resume downloads using it.
There is also a feature to do a Mirror Search. So it can download from several sources at the same time, maximising speed.

As for doing it in Linux, im not sure. Haven't tried to be honest. 
You could always try it in Wine :lol:

---

### Post by gs_berg on 2008-05-09
Thank you, I will try it in Wine.

But I would also like to know if there is way to do that in Ubuntu.  Also, I would like to use my saved files only to download the rest of the ISO file.

---

### Post by kpkeerthi on 2008-05-09
Linux has excellent native download managers. There is no need to wine any download managers.

**Graphical:**
d4x
multiget
downThemAll (firefox extension)
wxDownload
gwget

**Console-based:**
aria2
wget

Google to get more info about these. There is also **flashgot** firefox extension to integrate these with firefox.

As for resuming your broken ISO, I would simply do
```
cd /where/KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso.part/is/stored/
```
Rename it to .iso
```

mv KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso.part KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso

```
Resume it with -c option in wget
```
wget **-c** http://from.where.i.downloaded/KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso
```
Finally make sure MD5sums match.

Of course, you can use transmission/deluge/azureus bittorent clients. I recommend torrent for large downloads.

---

### Post by davidpbrown on 2008-05-09
Maybe try bittorrent.

-> [Use BitTorrent To Verify, Clean Up Files]("http://tech.slashdot.org/article.pl?sid=08/05/04/2230252")

---

### Post by gs_berg on 2008-05-09
Thanks kpkeerthi, you are a star.  Right now, I am watching the counter in the console finally moving from 75% upwards.  In a couple of hours, I will try new Knoppix.

Thanks everybody for inputs.

---

### Post by lengo on 2008-09-09
I've been trying to download virtualbox 1.6.6. The download has stalled about three times: once at 20MB, another at 18MB, and finally at 8MB. I started searching for how to restart a failed / broken download and learned about download managers (I found downthemall to be quite useless; DownTheMall as in DownTheGardenPath [I received an "error 400" at 88% and it would not continue]), torrents (though I still don't understand how to torrent . . . ), and finally wget. I have / had a partial file named: virtualbox_1.6.6-35336_Ubuntu_hardy_i386.deb?e=1220984160&h=706e80f587634b05db1ce5f8a23a0b3e
One tutorial said to rename it to virtualbox_1.6.6-35336_Ubuntu_hardy_i386.deb and:```

wget -c http://download.virtualbox.org/virtualbox/1.6.6/virtualbox_1.6.6-35336_Ubuntu_hardy_i386.deb
```
It just starts again at 0% with a new file name rather than continuing with the existing one . . . Another tutorial suggested:```

wget -np -r -c http://download.virtualbox.org/virtualbox/1.6.6/virtualbox_1.6.6-35336_Ubuntu_hardy_i386.deb
```
Same thing: no resume, just a new download to a new file. Any hints as to what I'm doing wrong? Thanks.

---

### Post by bingoUV on 2008-09-09
Glad to see you have solved your problem, but.

You seem to know how to resume a download in Fedora. The same method is extremely likely to work in Ubuntu. It would be a rare case where it will not work in Ubuntu but work in Fedora. Remember, linux is linux is linux.

---

### Post by lengo on 2008-09-09
> **bingoUV said:**
> Glad to see you have solved your problem, but.

You seem to know how to resume a download in Fedora. The same method is extremely likely to work in Ubuntu. It would be a rare case where it will not work in Ubuntu but work in Fedora. Remember, linux is linux is linux.
Um . . . the reason I'm posting is because I have *not* solved my problem. The two code snippets I provided did not work for me. Which is why I asked for more help. Perhaps I shouldn't have revived this thread? I don't know about what would work in Fedora as opposed to Ubuntu, but yes, I had assumed that linux was linux was linux (in the same way that a Ford is a Chevy is a Mazda is a Toyota).

---

### Post by greenhaven on 2008-11-21
> **kpkeerthi said:**
> Linux has excellent native download managers. There is no need to wine any download managers.

**Graphical:**
d4x
multiget
downThemAll (firefox extension)
wxDownload
gwget

**Console-based:**
aria2
wget

Google to get more info about these. There is also **flashgot** firefox extension to integrate these with firefox.

As for resuming your broken ISO, I would simply do
```
cd /where/KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso.part/is/stored/
```
Rename it to .iso
```

mv KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso.part KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso

```
Resume it with -c option in wget
```
wget **-c** http://from.where.i.downloaded/KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso
```
Finally make sure MD5sums match.

Of course, you can use transmission/deluge/azureus bittorent clients. I recommend torrent for large downloads.

This worked for me on a broken d/load of Yellowdog DVD at 50%. SEE THE POWER OF LINUX! Muwahahahahahahaha

---

### Post by GeorgeVita on 2009-07-12
> **kpkeerthi said:**
> Linux has excellent native download managers.
...
As for resuming your broken ISO, I would simply do
```
cd /where/KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso.part/is/stored/
```
Rename it to .iso
```

mv KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso.part KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso

```
Resume it with -c option in wget
```
wget **-c** http://from.where.i.downloaded/KNOPPIX_V5.3.1DVD-2008-03-26-EN.iso
```
Finally make sure MD5sums match.

Of course, you can use transmission/deluge/azureus bittorent clients. I recommend torrent for large downloads.

**This must be sticky to any Xxxx Xxxxx Testing and Discussion forum!**

wget is already installed into 9.10

I am using ONLY mobile broadband and I managed to continue a 'stopped' 9.10 daily .iso from 75% ...!
Downloading with up to 50KBytes/s after 2 1/2 hours stopped...

Many thanks to **kpkeerthi**,
George

---

### Post by vinutux on 2009-07-12
> **skymera said:**
> In Windows, Yes there is a way to resume downloads.
I use it for big files

[http://www.freedownloadmanager.org/](http://www.freedownloadmanager.org/)

You can stop, pause and resume downloads using it.
There is also a feature to do a Mirror Search. So it can download from several sources at the same time, maximising speed.

As for doing it in Linux, im not sure. Haven't tried to be honest. 
You could always try it in Wine :lol:


There is Multiget availabe for ubuntu

```
sudo apt-get install multiget
```


**[COLOR="DarkOrange"][http://multiget.sourceforge.net/]("http://multiget.sourceforge.net/")[/COLOR]**

..............................

---

