---
title: "Can't get android studio to work"
date: 2015-11-17
forum: General Help
---

### Post by sniffysniper on 2015-11-17
So I have been trying to get android studio to work, finally fixed the mkdscardtool error, but now I cannot finish the set up because of this?

Any clues?

[IMG]http://s29.postimg.org/rkjhjew93/Screenshot_from_2015_11_17_13_07_20.png[/IMG]

---

### Post by QDR06VV9 on 2015-11-17
With out knowing your method for install and what version of ubuntu IE Trusty(14.04) Vivid(15.04) or Wily(15.10)
See if this is of any help below.
 [https://paolorotolo.github.io/android-studio/](https://paolorotolo.github.io/android-studio/)
And you will need to install this also If you have not already.
```
[FONT=Consolas]sudo apt-get install lib32stdc++6[/FONT]
```
I have installed it on Trusty, and it works well.
More Info here [https://github.com/PaoloRotolo/android-studio#faq](https://github.com/PaoloRotolo/android-studio#faq)
> ~$ apt-cache policy android-studioandroid-studio:
  Installed: 4.11.0-ubuntu0
  Candidate: 4.11.0-ubuntu0
  Version table:
 *** 4.11.0-ubuntu0 0
        100 /var/lib/dpkg/status
me@me-Aspire-M3300:~$ 

**EDIT: **Just a heads up OpenJDK 6 is not supported. Please use Oracle Java or newer OpenJDK
If you want Oracle Java see this [FONT=Arial]using [/FONT][WebUpd8 PPA]("https://launchpad.net/~webupd8team/+archive/ubuntu/java")[FONT=Arial].
[/FONT]```
[FONT=Consolas]sudo add-apt-repository ppa:webupd8team/java[/FONT]
sudo apt-get update
sudo apt-get install oracle-java8-installer 
sudo apt-get install oracle-java8-set-default
```Regards

---

### Post by kostkon on 2015-11-17
[Ubuntu Make]("https://wiki.ubuntu.com/ubuntu-make") will make it easier for you to install Android Studio (and other popular development tools).

---

### Post by sniffysniper on 2015-11-21
Thank's for the replies!

So i'm on 15.10, but still have the issue 

"The SDK location is inside the Studio install location" ...

I already use the oracle jdk 8

edit: so i used ubuntu make that works... I don't know why.

---

### Post by QDR06VV9 on 2015-11-21
> **sniffysniper said:**
> Thank's for the replies!

So i'm on 15.10, but still have the issue 

edit: so i used ubuntu make that works... I don't know why.
Yes that is a new one on me also. Thanks for the share, And thanks to [COLOR=#000000]kostkon for pointing to it.
[/COLOR]Although with 3 installs here, never have I needed ubuntu make??
I will keep it in mind from now on.
Regards

---

