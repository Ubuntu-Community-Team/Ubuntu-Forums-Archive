---
title: "Avidemux?"
date: 2016-07-19
forum: General Help
---

### Post by sasafrass452 on 2016-07-19
I noticed that Avidemux is no longer available. After some research, I read that it's not compatible with 16.04, or words to that effect. Is this correct? If I install it from another repository, will it run smoothly? I won't bother if it's going to cause issues.... If I can't use Avidemux, is there another video editor that allows scanning videos frame-by-frame, & easily highlighting a portion to cut out if I choose to do so?

---

### Post by sudodus on 2016-07-19
I suggest that you try [openshot](http://www.openshot.org/)

```
sudo apt-get install openshot
```

I have used previous versions of openshot, and it works well for me. I have installed it but not really used it in 16.04 LTS yet.

---

### Post by sasafrass452 on 2016-07-19
I tried that, but it seems a bit hard to figure out how to use it. It also doesn't seem to let me scan frame by frame, & I can't figure out how to cut a scene. It's a little too complicated for me....

> **sudodus said:**
> I suggest that you try [openshot]("http://www.openshot.org/")

```
sudo apt-get install openshot
```

I have used previous versions of openshot, and it works well for me. I have installed it but not really used it in 16.04 LTS yet.

---

### Post by sudodus on 2016-07-19
I learned it by trial and error. There is information on the internet, search for ***openshot tutorial***, and you will find useful links.

---

### Post by mcduck on 2016-07-19
Here's a PPA with Avidemux for 16.04: [https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial]("https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial") Works great, and considering how much more capable it's in dealing with video formats, conversions, and especially being able to cut & demux video without having to re-encode it (no loss in quality and much, much less time consuming) it's worth having around even if that means using unofficial PPA... :D

---

### Post by sasafrass452 on 2016-07-20
Got it, thanx!!!

> **mcduck said:**
> Here's a PPA with Avidemux for 16.04: [https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial](https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial) Works great, and considering how much more capable it's in dealing with video formats, conversions, and especially being able to cut & demux video without having to re-encode it (no loss in quality and much, much less time consuming) it's worth having around even if that means using unofficial PPA... :D

Synaptic can't check for updates from this repository because it's not signed/verified. However, I can't find a way to add the signing key. I tried to follow the directions to add the repository with terminal, but it added it without the key despite the directions saying terminal would do this automatically. Help!

---

### Post by howefield on 2016-07-26
The signing key is on that ppa page.

You could copy the contents of the key to a text file and import with Software & Updates > Authentication > Import Key File.

Using..

sudo add-apt-repository ppa:rebuntu16/avidemux+unofficial does appear to load the key as expected.

```
hugh@xenial:~$ sudo add-apt-repository ppa:rebuntu16/avidemux+unofficial
[sudo] password for hugh: 
 EN: Here is a PPA for Avidemux, a good successor of Virtualdub. The following packages should be well enough for daily usage. Have fun using it !
I'm also working on the latest commits from the Github repository (third link).
Any bug when installing ? Please, contact me.

NOTE: libavidemux2.6(-unstable)-dev package is still not multi-arch. Using pkg-config files should solve this problem.

FR: Ce PPA est consacré à Avidemux, un Virtualdub-like. Les paquets devraient être suffisamment bons pour une utilisation quotidienne. Amusez-vous bien !
Je travaille également sur les dernières révisions à partir des dépôts Github (troisième lien).
Des soucis à l'installation ? N'hésitez pas à m'en parler.

http://avidemux.org/
https://github.com/mean00/avidemux2
http://aepatrakov.narod.ru/index/0-2
https://github.com/vapoursynth/vapoursynth
https://github.com/tesseract-ocr/tesseract
http://www.leptonica.org
https://github.com/sekrit-twc/zimg
 More info: https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpcia6jmo1/secring.gpg' created
gpg: keyring `/tmp/tmpcia6jmo1/pubring.gpg' created
gpg: requesting key 98F78EB3 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpcia6jmo1/trustdb.gpg: trustdb created
gpg: key 98F78EB3: public key "Launchpad PPA for Nguyen Thanh Tung" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
hugh@xenial:~$  sudo apt update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                                           
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]                                                    
Hit:4 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease                                                                       
Get:5 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial InRelease [17.6 kB]
Get:6 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages [27.2 kB]
Get:7 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main i386 Packages [27.1 kB]
Get:8 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main Translation-en [5,584 B]
Ign:9 http://dl.google.com/linux/talkplugin/deb stable InRelease                 
Hit:10 http://dl.google.com/linux/talkplugin/deb stable Release
Fetched 268 kB in 1s (161 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
hugh@xenial:~$ 
```

---

### Post by sasafrass452 on 2016-07-26
OOOHHH, I see.... I added the repo using this link: [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu). It didn't add the key as I expected. I tried your link, & it worked!!! Thanx!!!

> **howefield said:**
> The signing key is on that ppa page.

You could copy the contents of the key to a text file and import with Software & Updates > Authentication > Import Key File.

Using..

sudo add-apt-repository ppa:rebuntu16/avidemux+unofficial does appear to load the key as expected.

```
hugh@xenial:~$ sudo add-apt-repository ppa:rebuntu16/avidemux+unofficial
[sudo] password for hugh: 
 EN: Here is a PPA for Avidemux, a good successor of Virtualdub. The following packages should be well enough for daily usage. Have fun using it !
I'm also working on the latest commits from the Github repository (third link).
Any bug when installing ? Please, contact me.

NOTE: libavidemux2.6(-unstable)-dev package is still not multi-arch. Using pkg-config files should solve this problem.

FR: Ce PPA est consacré à Avidemux, un Virtualdub-like. Les paquets devraient être suffisamment bons pour une utilisation quotidienne. Amusez-vous bien !
Je travaille également sur les dernières révisions à partir des dépôts Github (troisième lien).
Des soucis à l'installation ? N'hésitez pas à m'en parler.

http://avidemux.org/
https://github.com/mean00/avidemux2
http://aepatrakov.narod.ru/index/0-2
https://github.com/vapoursynth/vapoursynth
https://github.com/tesseract-ocr/tesseract
http://www.leptonica.org
https://github.com/sekrit-twc/zimg
 More info: https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpcia6jmo1/secring.gpg' created
gpg: keyring `/tmp/tmpcia6jmo1/pubring.gpg' created
gpg: requesting key 98F78EB3 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpcia6jmo1/trustdb.gpg: trustdb created
gpg: key 98F78EB3: public key "Launchpad PPA for Nguyen Thanh Tung" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
hugh@xenial:~$  sudo apt update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                                           
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]                                                    
Hit:4 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease                                                                       
Get:5 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial InRelease [17.6 kB]
Get:6 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages [27.2 kB]
Get:7 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main i386 Packages [27.1 kB]
Get:8 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main Translation-en [5,584 B]
Ign:9 http://dl.google.com/linux/talkplugin/deb stable InRelease                 
Hit:10 http://dl.google.com/linux/talkplugin/deb stable Release
Fetched 268 kB in 1s (161 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
hugh@xenial:~$ 
```

---

