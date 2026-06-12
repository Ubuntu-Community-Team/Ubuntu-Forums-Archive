---
title: "Is it safe to remove libreoffice-gnome and libreoffice-gkt?"
date: 2015-08-14
forum: General Help
---

### Post by goghvv on 2015-08-14
Hi.
Is it safe two remove the two packages mentioned in the title?
What do they do? 

The reason I'm asking is that I too suffer from[ this annoying bug]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1246583"), and the last person to comment there says:

> In ubuntu 14.04 libreoffice 4.2.7.2 I have removed libreoffice-gnome and  libreoffice-gkt packges and it have solved the problem. Now when i use  Hebrew layout the kaybord shrtcuts are working.  My problem before this  removal was only within libreoffice applications so i think this bug is  not a duplicate of [bug #1226962]("https://bugs.launchpad.net/bugs/1226962")

But I want to be sure that the removal of these packages will not cause LibreOffice to function improperly, nor will it affect the stability of the os system.

Thanks in advance.

---

### Post by monkeybrain20122 on 2015-08-14
LO 4.2.x is end of life and your bug has been long fixed upstream apparently [https://bugs.documentfoundation.org/show_bug.cgi?id=41169&redirected_from=fdo](https://bugs.documentfoundation.org/show_bug.cgi?id=41169&redirected_from=fdo)

Just update LO [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

---

### Post by goghvv on 2015-08-14
Great!
They didn't mention how do I install LibreOfiice Fresh after adding the PPA to my system. Can you please help me with that?

By the way, If this bug was fixed long ago, how come the new version of LibreOffice is not included in my Ubuntu 14.04?

Thanks for your help.

---

### Post by monkeybrain20122 on 2015-08-14
Hi, In  the terminal type. 
```
sudo add-apt-respository ppa:libreoffice/ppa
sudo apt-get update 
sudo apt-get upgrade
```
The first line add the ppa to your source (which you probably have done already), the second line update the database, the third line upgrade LO

Ubuntu doesn't do version/feature updates. If your software is broken then it stays broken until the next release normally, some bug fixes may get backported if system related but not end user applications usually (so 2 years for LTS, or 5 years if you use the same LTS for all its lifespan). It only does security updates.

---

### Post by goghvv on 2015-08-14
Thanks again for your help.

It is certainly looks like it was doing something:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-impress libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-l10n-he libreoffice-math libreoffice-pdfimport
  libreoffice-style-human libreoffice-writer python3-uno uno-libs3 ure
The following packages will be upgraded:
  fonts-opensymbol liblcms2-2 libreoffice-ogltrans
  libreoffice-presentation-minimizer tzdata tzdata-java
6 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
Need to get 865 kB of archives.
After this operation, 147 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) trusty-updates/main tzdata-java all 2015f-0ubuntu0.14.04 [69.2 kB]
Get:2 [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) trusty-updates/main tzdata all 2015f-0ubuntu0.14.04 [171 kB]
Get:3 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main liblcms2-2 amd64 2.6-3ubuntu1~trusty1 [134 kB]
Get:4 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main fonts-opensymbol all 2:102.6+LibO5.0.0~rc5-0ubuntu1~trusty1 [278 kB]
Get:5 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main libreoffice-ogltrans amd64 1:5.0.0~rc5-0ubuntu1~trusty1 [135 kB]
Get:6 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main libreoffice-presentation-minimizer all 1:5.0.0~rc5-0ubuntu1~trusty1 [78.6 kB]
Fetched 865 kB in 1s (569 kB/s)                            
Preconfiguring packages ...
(Reading database ... 498894 files and directories currently installed.)
Preparing to unpack .../liblcms2-2_2.6-3ubuntu1~trusty1_amd64.deb ...
Unpacking liblcms2-2:amd64 (2.6-3ubuntu1~trusty1) over (2.5-0ubuntu4) ...
Preparing to unpack .../tzdata-java_2015f-0ubuntu0.14.04_all.deb ...
Unpacking tzdata-java (2015f-0ubuntu0.14.04) over (2015d-0ubuntu0.14.04) ...
Preparing to unpack .../tzdata_2015f-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2015f-0ubuntu0.14.04) over (2015d-0ubuntu0.14.04) ...
Setting up tzdata (2015f-0ubuntu0.14.04) ...

Current default time zone: 'Asia/Jerusalem'
Local time is now:      &#1493;' &#1488;&#1493;&#1490; 14 12:35:40 IDT 2015.
Universal Time is now:  Fri Aug 14 09:35:40 UTC 2015.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 498895 files and directories currently installed.)
Preparing to unpack .../fonts-opensymbol_2%3a102.6+LibO5.0.0~rc5-0ubuntu1~trusty1_all.deb ...
Unpacking fonts-opensymbol (2:102.6+LibO5.0.0~rc5-0ubuntu1~trusty1) over (2:102.6+LibO4.2.8-0ubuntu2) ...
Preparing to unpack .../libreoffice-ogltrans_1%3a5.0.0~rc5-0ubuntu1~trusty1_amd64.deb ...
Unpacking libreoffice-ogltrans (1:5.0.0~rc5-0ubuntu1~trusty1) over (1:4.2.8-0ubuntu2) ...
Preparing to unpack .../libreoffice-presentation-minimizer_1%3a5.0.0~rc5-0ubuntu1~trusty1_all.deb ...
Unpacking libreoffice-presentation-minimizer (1:5.0.0~rc5-0ubuntu1~trusty1) over (1:4.2.8-0ubuntu2) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Processing triggers for libreoffice-common (1:4.2.8-0ubuntu2) ...
Setting up liblcms2-2:amd64 (2.6-3ubuntu1~trusty1) ...
Setting up tzdata-java (2015f-0ubuntu0.14.04) ...
Setting up fonts-opensymbol (2:102.6+LibO5.0.0~rc5-0ubuntu1~trusty1) ...
Setting up libreoffice-ogltrans (1:5.0.0~rc5-0ubuntu1~trusty1) ...
Setting up libreoffice-presentation-minimizer (1:5.0.0~rc5-0ubuntu1~trusty1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
$
```

But when I open LibreOffice, there's still no change (even after a reboot):

[IMG]http://s22.postimg.org/9dcytvsa9/libre.png[/IMG]


And needless to say the bug is still there...
 
Do you have any idea how to proceed?

---

### Post by monkeybrain20122 on 2015-08-14
Hmm. strange. It seems that it only upgraded the themes and fonts but the actual software (LO) is being held back. I have no idea why.

Edited: did you run sudo apt-get update before sudo apt-get upgrade?

---

### Post by goghvv on 2015-08-14
> **monkeybrain20122 said:**
> Hmm. strange. It seems that it only upgraded the themes and fonts but the actual software (LO) is being held back. I have no idea why.

Do you refer to these lines:

```
The following packages have been kept back:
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-impress libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-l10n-he libreoffice-math libreoffice-pdfimport
  libreoffice-style-human libreoffice-writer python3-uno uno-libs3 ure
```

If so, is there a way to force it to install these packages?

---

### Post by goghvv on 2015-08-14
> **monkeybrain20122 said:**
> Hmm. strange. It seems that it only upgraded the themes and fonts but the actual software (LO) is being held back. I have no idea why.

Edited: did you run sudo apt-get update before sudo apt-get upgrade?

Pretty sure I did, but let me try again...

---

### Post by goghvv on 2015-08-14
Yep. This still doesn't help...
Now the upgrade command just shows this:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-impress libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-l10n-he libreoffice-math libreoffice-pdfimport
  libreoffice-style-human libreoffice-writer python3-uno uno-libs3 ure
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
$
```

Which is indeed very strange...

---

### Post by goghvv on 2015-08-14
OK!
I googled it around, and found [this]("http://askubuntu.com/questions/407326/problems-while-doing-sudo-apt-get-upgrade") to be helpful.
It solved my problem. :)

Thanks for your help!

---

### Post by goghvv on 2015-08-14
OK, I guess it was too soon to be happy.
It did install libreoffice5, but the bug is still there... :\
Oh well, I think I''ll just learn to live with it.

---

### Post by monkeybrain20122 on 2015-08-14
Maybe should start a new bug there.

---

