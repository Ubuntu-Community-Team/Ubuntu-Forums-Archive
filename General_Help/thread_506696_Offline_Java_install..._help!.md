---
title: "Offline Java install... help!"
date: 2007-07-22
forum: General Help
---

### Post by tnunamak on 2007-07-22
I've been trying to install Java and then the plug in for firefox so I can get pass my school's authentication  barrier but I can't connect to the internet until I do, so I have to copy files from another computer and install not using apt-get or synaptic.

I tried downloading the script/sh file from sun's website, and it appeared to install correctly, but it doesn't look it like it actually is installed. I also have been trying to copy over packages like sun-java6-bin but I ran into a problem with that one conflicting with sun-java6-jre... the two packages depend on each other so I can't install either.

Please help!

edit: got it using help from [https://help.ubuntu.com/community/Firefox2AMD64Flash9Java#head-16e29d0ec0a7c327680960988bbae2c60034d78e](https://help.ubuntu.com/community/Firefox2AMD64Flash9Java#head-16e29d0ec0a7c327680960988bbae2c60034d78e)

---

### Post by zanglang on 2007-07-22
Just curious, but why do you need Java to get on to the internet?

Anyway, you can try downloading the .deb files manually when you do get online and then installing them offline. All related packages for Java 6 is available here (Assuming you use Feisty ;)):
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sun-java6&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sun-java6&searchon=names&subword=1&version=feisty&release=all)
If you're not sure which ones you'll need, try installing sun-java6-jre from Synaptic or aptitude and see which additional packages does it require, download those as well.

When you're done, you can either copy them into /var/cache/apt/archives, or use "sudo dpkg -i sun-java6-*.deb" to install them.

---

