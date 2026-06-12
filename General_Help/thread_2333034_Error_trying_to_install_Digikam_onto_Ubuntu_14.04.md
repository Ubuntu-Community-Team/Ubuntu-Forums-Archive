---
title: "Error trying to install Digikam onto Ubuntu 14.04"
date: 2016-08-06
forum: General Help
---

### Post by kologha on 2016-08-06
Error message was: 'Error: Broken Count >0'

There is a red No Entry symbol at the top right of the screen, I am afraid I understand very little regarding using the terminal code. What to do now?

---

### Post by theonlytalkinggoat on 2016-08-06
Did you install this from the dev's PPA?

---

### Post by kologha on 2016-08-06
I first downloaded and installed Digikam from Ubuntu Software Centre and it placed an icon on the left of the screen, but I could not get Digicam to run. I looked on the Internet and ended up loading another Digicam and had to go to a web page to get a PPS or something and then I got this error and now I'm hopelessly lost!!! I would appreciate some help. I have to keep dual booting to Win XP in order to upload photos and I wanted a photo programme which could upload photos from my camera in Ubuntu.

---

### Post by theonlytalkinggoat on 2016-08-06
Did you remove and purge the old version, before you installed the new one? 

At the command line, type: 
apt-cache policy | grep philip5

---

### Post by kologha on 2016-08-07
No I didn't remove or purge the old one.
 The result of typing in 'apt-cache policy | grep philip5' 				

user@user-O-E-M:~$ apt-cache policy | grep philip5 
 500 [http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu/](http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu/) trusty/main Translation-en
 500 [http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu/](http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu/) trusty/main i386 Packages
     release v=14.04,o=LP-PPA-philip5-kubuntu-backports,a=trusty,n=trusty,l=kubuntu-backports,c=main
 500 [http://ppa.launchpad.net/philip5/extra/ubuntu/](http://ppa.launchpad.net/philip5/extra/ubuntu/) trusty/main Translation-en
 500 [http://ppa.launchpad.net/philip5/extra/ubuntu/](http://ppa.launchpad.net/philip5/extra/ubuntu/) trusty/main i386 Packages
     release v=14.04,o=LP-PPA-philip5-extra,a=trusty,n=trusty,l=extra,c=main

What now?

---

### Post by kologha on 2016-08-07
[SOLVED] I have solved my problem thanks.

---

### Post by wildmanne39 on 2016-08-07
Please share how you fixed you problem so anyone else looking for the answer to the same problem can solve their problem too.
Thanks

---

