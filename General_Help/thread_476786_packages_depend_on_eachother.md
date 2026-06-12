---
title: "packages depend on eachother"
date: 2007-06-17
forum: General Help
---

### Post by zorkerz on 2007-06-17
Hi All
I have xubuntu installed on my dads computer. I am trying to get the modem to work. To do this I havd been asked to install build-essential which depends on g++. g++ in turn depends on g++-4.1 which depends on libstdc++6-4.1-dev. This is where my problem begins.

libstdc++6-4.1-dev depends on g++-4.1 but g++-4.1 depends on libstdc++6-4.1-dev.
I don't have internet on this computer so i have downloaded the .debs and am trying to install them with gdebi which is apparently unable to handle this circular codependencies.

How can I install these packages?

I tried to "add downloaded packages" in synaptic but it will not let me select the packages.

Thanks

---

### Post by zorkerz on 2007-06-17
so ive been messing around a bit with no real luck.
/var/cache/apt/archives is the location of archived debs for apt-get and synaptic
I added my packages here hoping that it would allow synaptic to recognize them because it does not seem to ever have my current dependence problem. However I dont know what to do to get apt-get to look here for packages instead of online.
any ideas

---

### Post by WW on 2007-06-17
g++-4.1 also depend on gcc-4.1, gcc-4.1-base, and libc6.  If you have successfully installed these, you could try installing g++-4.1 with the **dpkg** command.  Warning: the following suggestion is based on reading the manpage, not on personal experience:
```

$ sudo dpkg -i --ignore-depends=libstdc++6-4.1-dev   g++-4.1.??????.deb

```
(Change g++-4.1.??????.deb to the actual filename.)  If that works, then you should be able to install libstdc++6-4.1.dev.

---

### Post by zorkerz on 2007-06-17
Thanks Alot WW.
This worked wonderfully. 
I had to also use dpkg to install libstdc++6-4.1.dev as all other programs did not like the broken dependencies and it all went smoothly.
cheers

---

### Post by WW on 2007-06-17
For what it's worth, I filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/120935](https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/120935)

---

### Post by zorkerz on 2007-06-18
great idea i have subscribed to it

---

### Post by Bachstelze on 2007-06-18
This is not the proper way to install b-e, as it is on your Ubuntu CD. Do :

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo touch /etc/apt/sources.list
sudo apt-cdrom add
***** Insert your Ubuntu CD here *****
sudo apt-get install build-essential
```

---

### Post by zorkerz on 2007-06-18
this is a good point i did not even think of using a cd. Would this be on my xubuntu cd as well? I don't know the extent of the differences between these. I have ubuntu cds as well and eitherway my problem is solved. It seems to me downloading debs is a valid way to install packages and it is simply gdebi that does not have the functionality to deal with it.

Also a better way to have solved this i now see from the bug report would have been to give dpkg both debs at the same time. This would not have broken anything even temporarily i believe. 

This make sense?

---

