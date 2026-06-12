---
title: "installing sipp in ubuntu 10.10"
date: 2013-04-17
forum: General Help
---

### Post by mahanew on 2013-04-17
Hi,
I want to install voip packet generator sipp.To do so ,i have first to install  those packages:
[FONT=Verdana]sudo apt-get install libssl-dev libpcap-dev libncurses5-dev
[/FONT]

But ,I always receive the same problem
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main libssl0.9.8 i386 0.9.8o-1ubuntu4.6
  404  Not Found
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main libncurses5-dev i386 5.7+20100626-0ubuntu1
  404  Not Found
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main zlib1g-dev i386 1:1.2.3.4.dfsg-3ubuntu1
  404  Not Found
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main libssl0.9.8 i386 0.9.8o-1ubuntu4.6
  404  Not Found [IP : 91.189.92.181 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main libssl-dev i386 0.9.8o-1ubuntu4.6
  404  Not Found [IP : 91.189.92.181 80]
Impossible de récupérer [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-1ubuntu4.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-1ubuntu4.6_i386.deb)  404  Not Found [IP : 91.189.92.181 80]
Impossible de récupérer [http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5-dev_5.7+20100626-0ubuntu1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5-dev_5.7+20100626-0ubuntu1_i386.deb)  404  Not Found
Impossible de récupérer [http://fr.archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g-dev_1.2.3.4.dfsg-3ubuntu1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g-dev_1.2.3.4.dfsg-3ubuntu1_i386.deb)  404  Not Found
Impossible de récupérer [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8o-1ubuntu4.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8o-1ubuntu4.6_i386.deb)  404  Not Found [IP : 91.189.92.181 80]

Please I nead your help.Thank you so much

---

### Post by oldos2er on 2013-04-17
10.10 is no longer supported, so its repositories have moved to old-releases, see [http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions](http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions)

You really should upgrade to a supported version.

---

### Post by mahanew on 2013-04-17
Thank you for your help.But please help me.Which version do I choose?

---

### Post by mörgæs on 2013-04-18
Please run **sudo lshw > lshw.txt** and post lshw.txt in CODE tags.

---

### Post by mahanew on 2013-04-18
In fact, I have installed it from a friend's CD .
Should I choose another version?
In fact ,I have 2 versions of ubuntu(working at 2 pc):the first one is 10.10 and the other one is 12.04TLS.Should I work only with 12.04TLS?

---

### Post by mörgæs on 2013-04-18
Yes. You can use anything that's supported, 12.04 or another one, but 10.10 should go.

If Ubuntu is too slow then Xubuntu is an option. Here is the support scheme:

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)
[http://en.wikipedia.org/wiki/Xubuntu#Releases](http://en.wikipedia.org/wiki/Xubuntu#Releases)

---

### Post by mahanew on 2013-04-18
Thank you so much.But ,I have other  problem(Sorry if I bother you)
I'm using also ubuntu 12.4TLS (as I told you)  and i want to install build-essential.So ,I do  so from the sit ubuntu packages using software center.but I have this  problem dependancy is not satisfiable:g++(>=4:4.4.3) .Maybe it's a  problem of dependency ? I am using libc6 (2.15-0ubuntu10.3)while the version that must be  installed with ubuntu 12.04(precise) is libc6 (2.15-0ubuntu10.2).Is that  the problem? Please please please I need your help.

---

### Post by mörgæs on 2013-04-18
No, you need patience. That question is being dealt with in your other thread.

---

### Post by mahanew on 2013-04-19
Bonjour, 

J'ai installer libc-bin 2.15-0ubuntu10.3 et j'ai besoin de la version 2.15-0ubuntu10.2 afin d'installer libc6 2.15-0ubuntu10.2 .
Que dois-je faire?
J'ai vraiment besoin de votre aide.

Merci d'avanace

---

### Post by mörgæs on 2013-04-19
Again: For the installation problem you should follow the advice given in the other thread. 

If you prefer help in another language than English it's better to post in a [local forum]("http://ubuntuforums.org/forumdisplay.php?f=183"), but don't raise the same question again.

Thread closed.

---

