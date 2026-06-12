---
title: "Can't install FFMPEG on Ubuntu Server 14.04"
date: 2015-07-07
forum: General Help
---

### Post by roadwarrior2 on 2015-07-07
I am trying to install FFMPEG but I always get some sort of error. I am using these commands that I got from [http://www.noobslab.com/2014/12/ffmpeg-returns-to-ubuntu-1410.html](http://www.noobslab.com/2014/12/ffmpeg-returns-to-ubuntu-1410.html)       ```
sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next
sudo apt-get update
sudo apt-get install ffmpeg
```  
These are the results: 
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


  The following packages have unmet dependencies:
 ffmpeg : Depends: libavcodec54 (>= 8:1.0.0) but it is not going to be installed
          Depends: libavdevice54 (>= 8:1.0.0) but it is not going to be installed
          Depends: libavfilter3 (>= 8:1.0.0) but 6:9.18-0ubuntu0.14.04.1 is to be installed
          Depends: libavformat54 (>= 8:1.0.0) but 6:9.18-0ubuntu0.14.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by QDR06VV9 on 2015-07-07
How Odd? There is another PPA that is put together by one of our very own members here in the forums witch I use.
But you may have to remove any changes made with the PPA you were trying
So you would purge that PPA by
```
sudo ppa-purge ppa:kirillshkrogalev/ffmpeg-next
```
Followed by 
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
```
Then to add his PPA More Info Here [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get dist-upgrade


```
See if that gets you sorted out.
Regards

---

### Post by mc4man on 2015-07-07
It should install from that ppa even though the build is quite outdated. ffmpeg would not depend on what you've posted,  more like libavcodec-ffmpeg56, libavformat-ffmpeg56, ect. 
So maybe your sources are a bit out of date too?
what does this show - 
```
apt-cache policy ffmpeg
```

Otherwise - why do you want ffmpeg & do you require a shared version? (shared libs from ffmpeg will not be used unless sources that could use them are specifically built off of the shared ffmpeg headers.

---

### Post by roadwarrior2 on 2015-07-08
```
 apt-cache policy ffmpeg
ffmpeg:
  Installed: (none)
  Candidate: 8:1.0.10-dmo1
  Version table:
     8:1.0.10-dmo1 0
        500 http://www.deb-multimedia.org/ wheezy/main amd64 Packages
     7:2.7.1+git1~trusty1 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main
amd64 Packages
```

---

### Post by roadwarrior2 on 2015-07-08
I still get the same issues. I need ffmpeg to convert audio files trough Headphones (for downloading and organizing music)

---

### Post by mc4man on 2015-07-08
If you use the Debian deb multimedia ppa in Ubuntu then issues will not be uncommon & generally it's a poor practice. I'd remove it from your sources.
You can get newer & better packages from any number of Ubuntu ppa's. 
For ffmpeg the latest git in the ppa mentioned above, ist use of that ppa should be done with a sudo dist-upgrade command, reading ppa page is advised. (that ffmpeg is a static version meant for use of the ffmpeg binaires, ie. ffmpeg, ffplay, ffprobe, ffserver

Or go here, download/extract & use the prebuilt standalone ffmpeg binaries, done like a portable app - 
[http://johnvansickle.com/ffmpeg/](http://johnvansickle.com/ffmpeg/)

If you need newer shared ffmpeg libraries for some app to use then again there are some ppa's better than the one you are trying to use & better than deb multimedia, just ask.

---

### Post by monkeybrain20122 on 2015-07-08
I used this ffmpeg ppa for 14.04 [https://launchpad.net/~samrog131/+archive/ubuntu/ppa](https://launchpad.net/~samrog131/+archive/ubuntu/ppa) It is shared ffmpeg and up tp date.

---

### Post by mc4man on 2015-07-08
> **monkeybrain20122 said:**
> I used this ffmpeg ppa for 14.04 [https://launchpad.net/~samrog131/+archive/ubuntu/ppa](https://launchpad.net/~samrog131/+archive/ubuntu/ppa) It is shared ffmpeg and up tp date.
That ppa is going to be dead soon... 
I don't see the point in general of installing a shared ffmpeg unless one intends to rebuild sources off of it, either ppa provided or locally, otherwise the only thing using those shared libs is the ffmpeg binaries. Whether that is of any value to those binaries is questionable.

(- in the near future I believe Debian will be dropping Libav in favour of FFmpeg, Ubuntu will follow suit there. Some other distros have already returned to FFmpeg.

---

### Post by monkeybrain20122 on 2015-07-08
> **mc4man said:**
> That ppa is going to be dead soon... 
I don't see the point in general of installing a shared ffmpeg unless one intends to rebuild sources off of it, either ppa provided or locally, otherwise the only thing using those shared libs is the ffmpeg binaries. Whether that is of any value to those binaries is questionable.
.

I build mpv, vlc  and opencv from ffmpeg shared libraries.

P.S. didn't know that ppa is going to die soon. I am not using Trusty anymore. On Vivid I am using your ffmpeg-shared ppa, which is great.

---

### Post by bomberb17 on 2016-02-19
I tried the above but I can't get ffmpeg installed.
I also have Ubuntu server 14.04.
Can someone help?

```
 apt-get install ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ffmpeg' has no installation candidate


```

---

### Post by SeijiSensei on 2016-02-19
Which "above?"  Use Doug McMahon's repository as described in post #2 above: [http://ubuntuforums.org/showthread.php?t=2285676&p=13316760&viewfull=1#post13316760](http://ubuntuforums.org/showthread.php?t=2285676&p=13316760&viewfull=1#post13316760)

---

### Post by bomberb17 on 2016-02-19
> **SeijiSensei said:**
> Which "above?"  Use Doug McMahon's repository as described in post #2 above: [http://ubuntuforums.org/showthread.php?t=2285676&p=13316760&viewfull=1#post13316760](http://ubuntuforums.org/showthread.php?t=2285676&p=13316760&viewfull=1#post13316760)

I tried it but it won't install, I still get the same message..

---

### Post by SeijiSensei on 2016-02-19
Did you run a purge first?  
```
sudo apt-get remove --purge ffmpeg
```

Did you update your repo lists with "sudo apt-get update" after purging and using add-apt-repository?

```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install ffmpeg

```

I used these commands just now to install Doug's PPA and ffmpeg on a nearly new 14.04 Kubuntu machine.  It installed without a hitch.  I don't have a copy of Server conveniently available, but I doubt there is much that would distinguish the two versions when it comes to a command-line program like ffmpeg.

---

### Post by FakeOutdoorsman on 2016-02-19
Use mc4man's PPA as described by runrickus in post #2, or use the prebuilt ffmpeg binaries as described by mc4man in post #6.

Edit: Damn. Apparently I'm still learning how to use this forum. Thought I clicked on the "latest post" button and didn't see page 2.

---

### Post by bomberb17 on 2016-02-21
Ok I ran purge, then add-apt-repository. I get an "OK" at the end.
But after running apt-get update, I get :

```
root@odroid-server:/home/bomberb17# apt-get update
Ign http://ports.ubuntu.com trusty InRelease
Ign http://ppa.launchpad.net trusty InRelease
Get:1 http://ports.ubuntu.com trusty-updates InRelease [65.9 kB]
Ign http://ppa.launchpad.net saucy InRelease
Ign http://ppa.launchpad.net trusty InRelease
Hit http://ports.ubuntu.com trusty-backports InRelease
Hit http://ppa.launchpad.net trusty InRelease
Ign http://ppa.launchpad.net trusty Release.gpg
Hit http://ports.ubuntu.com trusty-security InRelease
Ign http://ppa.launchpad.net saucy Release.gpg
Hit http://ports.ubuntu.com trusty Release.gpg
Hit http://ppa.launchpad.net trusty Release.gpg
Get:2 http://ports.ubuntu.com trusty-updates/main Sources [260 kB]
Ign http://ppa.launchpad.net trusty Release
Ign http://ppa.launchpad.net saucy Release
Hit http://ppa.launchpad.net trusty Release
Hit http://ppa.launchpad.net trusty/main armhf Packages
Get:3 http://ports.ubuntu.com trusty-updates/restricted Sources [5352 B]
Hit http://ppa.launchpad.net trusty/main Translation-en
Get:4 http://ports.ubuntu.com trusty-updates/universe Sources [150 kB]
Get:5 http://ports.ubuntu.com trusty-updates/main armhf Packages [623 kB]
Hit http://ppa.launchpad.net trusty/main armhf Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Get:6 http://ports.ubuntu.com trusty-updates/restricted armhf Packages [8421 B]
Get:7 http://ports.ubuntu.com trusty-updates/universe armhf Packages [333 kB]
Get:8 http://ports.ubuntu.com trusty-updates/main Translation-en [356 kB]
Get:9 http://ports.ubuntu.com trusty-updates/restricted Translation-en [3699 B]
Get:10 http://ports.ubuntu.com trusty-updates/universe Translation-en [180 kB]
Hit http://ports.ubuntu.com trusty Release
Hit http://ports.ubuntu.com trusty-backports/main Sources
Hit http://ports.ubuntu.com trusty-backports/restricted Sources
Hit http://ports.ubuntu.com trusty-backports/main armhf Packages
Hit http://ports.ubuntu.com trusty-backports/restricted armhf Packages
Hit http://ports.ubuntu.com trusty-backports/main Translation-en
Hit http://ports.ubuntu.com trusty-backports/restricted Translation-en
Hit http://ports.ubuntu.com trusty-security/main Sources
Hit http://ports.ubuntu.com trusty-security/restricted Sources
Hit http://ports.ubuntu.com trusty-security/universe Sources
Hit http://ports.ubuntu.com trusty-security/multiverse Sources
Hit http://ports.ubuntu.com trusty-security/main armhf Packages
Hit http://ports.ubuntu.com trusty-security/restricted armhf Packages
Hit http://ports.ubuntu.com trusty-security/universe armhf Packages
Hit http://ports.ubuntu.com trusty-security/multiverse armhf Packages
Hit http://ports.ubuntu.com trusty-security/main Translation-en
Hit http://ports.ubuntu.com trusty-security/multiverse Translation-en
Hit http://ports.ubuntu.com trusty-security/restricted Translation-en
Err http://ppa.launchpad.net trusty/main armhf Packages
  404  Not Found
Hit http://ports.ubuntu.com trusty-security/universe Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en
Hit http://ports.ubuntu.com trusty/main Sources
Err http://ppa.launchpad.net saucy/main armhf Packages
  404  Not Found
Hit http://ports.ubuntu.com trusty/restricted Sources
Hit http://ports.ubuntu.com trusty/universe Sources
Ign http://ppa.launchpad.net saucy/main Translation-en
Hit http://ports.ubuntu.com trusty/main armhf Packages
Hit http://ports.ubuntu.com trusty/restricted armhf Packages
Hit http://ports.ubuntu.com trusty/universe armhf Packages
Hit http://ports.ubuntu.com trusty/main Translation-en
Hit http://ports.ubuntu.com trusty/restricted Translation-en
Hit http://ports.ubuntu.com trusty/universe Translation-en
Fetched 1985 kB in 12s (161 kB/s)
W: Failed to fetch http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/trusty/main/binary-armhf/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/saucy/main/binary-armhf/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@odroid-server:/home/bomberb17# apt-get install ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ffmpeg' has no installation candidate


```

How can i fix this?

---

### Post by SeijiSensei on 2016-02-21
> Failed to fetch [http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/saucy/main/binary-armhf/Packages](http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/dists/saucy/main/binary-armhf/Packages)

That's not the repository we mentioned above.  You want to be using this one:
```
sudo add-apt-repository ppa:mc3man/trusty-media
```
You can remove the severinsson repository with "add-apt-repository -r" or just delete (using sudo) the files associated with this repository from /etc/apt/sources.list.d/.  Then add McMahon's repository and run "sudo apt-get update".

---

