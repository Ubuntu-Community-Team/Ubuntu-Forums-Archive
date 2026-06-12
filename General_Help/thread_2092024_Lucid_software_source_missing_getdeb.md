---
title: "Lucid software source missing getdeb"
date: 2012-12-06
forum: General Help
---

### Post by Cavsfan on 2012-12-06
If any one else on Lucid is getting errors like this when trying **sudo apt-get update**:
```
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (113: No route to host)

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-amd64/Packages.gz  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
```The workaround is this:
In terminal enter **gksu gedit /etc/apt/sources.list.d/getdeb.list**
then replace the contents with this:
```
deb http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
```I just replaced the first line as I didn't have the source line but, that is up to you.
Then enter **sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A8A515F046D7E7CF**

Then enter **sudo apt-get update** to see if the error is gone.
I had been getting this error for the past couple of days. But, this fixed it for me.

If getting this error on another version of Ubuntu, just change lucid-getdeb to precise-getdeb or whatever suits your needs.
This even works on Linux Mint.
I hope this helps someone else with the same problem.

---

### Post by TheFu on 2012-12-06
10.04 is becoming non-supported. I've seen some important application PPAs have stopped releasing 10.04 binaries.  Thunderbird did this last week.

**In short, it is time to migrate to 12.04 sooner than later.**

---

### Post by SmilePiper on 2012-12-06
It's because GetDeb is down right now.  When ever their repositories go down, the site usually goes down with it.  You can check to see if their site is up or not by going to getdeb.net.  In the mean time, there are a few of the same games offered on dotdeb.com for download.

---

### Post by Cavsfan on 2012-12-07
> **TheFu said:**
> 10.04 is becoming non-supported. I've seen some important application PPAs have stopped releasing 10.04 binaries.  Thunderbird did this last week.

**In short, it is time to migrate to 12.04 sooner than later.**

Technically, Lucid will be officially supported until April 2013 for desktop and April 2015 for server.
Firefox was removed from the mozillateam/firefox-stable ppa about September 2012 that we had added to get updates for Firefox.
Thunderbird did the same later.
But, the normal Lucid repositories still provide updates for both Firefox and Thunderbird.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=2063647_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2063647")

I plan on hanging onto Lucid until just prior to April 2013 myself. I already have 2 Lucid 10.04 installs, 2 Precise 12.04 installs and 2 Quantal 12.10 installs along with Windows 7 on my Grub2 menu.
That green link in my signature has a picture of what my grub2 screen looks like.


> **SmilePiper said:**
> It's because GetDeb is down right now.  When ever their repositories go down, the site usually goes down with it.  You can check to see if their site is up or not by going to getdeb.net.  In the mean time, there are a few of the same games offered on dotdeb.com for download.

I agree and this is one workaround for that problem.

---

### Post by olegvf on 2012-12-09
> **Cavsfan said:**
> 
The workaround is this:
In terminal enter **gksu gedit /etc/apt/sources.list.d/getdeb.list**
then replace the contents with this:
```
deb http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
```I just replaced the first line as I didn't have the source line but, that is up to you.
Then enter **sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A8A515F046D7E7CF**

Then enter **sudo apt-get update** to see if the error is gone.
I had been getting this error for the past couple of days. But, this fixed it for me.

If getting this error on another version of Ubuntu, just change lucid-getdeb to precise-getdeb or whatever suits your needs.
This even works on Linux Mint.
I hope this helps someone else with the same problem.

Worked for me in Mint, though **getdeb.list** file was not present in the **/etc/apt/sources.list.d** directory. So, I just created it there then launched Software Sources and unchecked all getdeb.net entries.

Thank you

---

### Post by Cavsfan on 2012-12-09
> **olegvf said:**
> Worked for me in Mint, though **getdeb.list** file was not present in the **/etc/apt/sources.list.d** directory. So, I just created it there then launched Software Sources and unchecked all getdeb.net entries.

Thank you

You are welcome! I am glad it helped. That is why I posted it because I figured if I was getting that error in Ubuntu Lucid, 
others were getting it too.
I found the instructions for the fix in a Linux Mint Forum.

---

### Post by CCC999 on 2012-12-18
Thanks Cavsfan - worked perfectly on my precise box. One reason I recommend Linux is the community!

---

### Post by Cavsfan on 2012-12-19
> **CCC999 said:**
> Thanks Cavsfan - worked perfectly on my precise box. One reason I recommend Linux is the community!

You are welcome **CCC999**! I agree! there are always people here to help out. :)

---

