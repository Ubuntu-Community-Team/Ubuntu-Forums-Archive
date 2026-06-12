---
title: "Installing Java on Ubuntu 12.4 LTS  (help)"
date: 2012-10-18
forum: General Help
---

### Post by majorburt on 2012-10-18
i need some help with this.

i am trying to install Java onto my comp but i cant seem to be able to figure it out.:confused:

any help would be appreciated a lot. even better if the help could be simple to understand as i don't know a lot about the more complex stuff like command prompt.

---

### Post by GreenTaurus on 2012-10-18
[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html]("http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html")

---

### Post by lightning slinger on 2012-10-18
Or go to the wepupd8 page itself!

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by majorburt on 2012-10-18
so basically, i have to input
 this  (sudo add-apt-repository ppa:webupd8team/java) 
then this (sudo apt-get update) 
then this (sudo apt-get install oracle-java7-installer)
into the terminal, then it should be installed?

---

### Post by lightning slinger on 2012-10-18
Yes!
Current version is java version "1.7.0_09"

---

### Post by majorburt on 2012-10-18
chance@Chance-pc:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en linux-headers-3.2.0-29
  language-pack-kde-zh-hans language-pack-kde-en-base kde-l10n-engb
  linux-headers-3.2.0-29-generic-pae kde-l10n-zhcn language-pack-zh-hans-base
  firefox-locale-zh-hans language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11
Suggested packages:
  visualvm ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  gsfonts-x11 oracle-java7-installer
0 upgraded, 2 newly installed, 0 to remove and 17 not upgraded.
Need to get 26.3 kB of archives.
After this operation, 315 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://ppa.launchpad.net/webupd8team/java/ubuntu/](http://ppa.launchpad.net/webupd8team/java/ubuntu/) precise/main oracle-java7-installer all 7u9-0~webupd8~1
  Could not resolve 'ppa.launchpad.net'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gsfonts-x11 all 0.22
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/pool/main/o/oracle-java7-installer/oracle-java7-installer_7u9-0~webupd8~1_all.deb](http://ppa.launchpad.net/webupd8team/java/ubuntu/pool/main/o/oracle-java7-installer/oracle-java7-installer_7u9-0~webupd8~1_all.deb)  Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.22_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.22_all.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



what does it mean?
 it looks like there were errors towards the bottom, is it just a loss of Internet connection?

---

### Post by majorburt on 2012-10-18
> **majorburt said:**
> chance@Chance-pc:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en linux-headers-3.2.0-29
  language-pack-kde-zh-hans language-pack-kde-en-base kde-l10n-engb
  linux-headers-3.2.0-29-generic-pae kde-l10n-zhcn language-pack-zh-hans-base
  firefox-locale-zh-hans language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11
Suggested packages:
  visualvm ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  gsfonts-x11 oracle-java7-installer
0 upgraded, 2 newly installed, 0 to remove and 17 not upgraded.
Need to get 26.3 kB of archives.
After this operation, 315 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://ppa.launchpad.net/webupd8team/java/ubuntu/](http://ppa.launchpad.net/webupd8team/java/ubuntu/) precise/main oracle-java7-installer all 7u9-0~webupd8~1
  Could not resolve 'ppa.launchpad.net'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gsfonts-x11 all 0.22
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/pool/main/o/oracle-java7-installer/oracle-java7-installer_7u9-0~webupd8~1_all.deb](http://ppa.launchpad.net/webupd8team/java/ubuntu/pool/main/o/oracle-java7-installer/oracle-java7-installer_7u9-0~webupd8~1_all.deb)  Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.22_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.22_all.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



what does it mean?
 it looks like there were errors towards the bottom, is it just a loss of Internet connection?
it was just a loss of connection.
its installing now.

---

### Post by majorburt on 2012-10-18
its installed, but its asking for (Java JRE).
 i have the 45.7 package labeled (Linux) from ([http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en))

how do i mount it, it looks like an archive or a zip but its a (.tar.gz)

---

### Post by lightning slinger on 2012-10-19
Not sure what's gone wrong with your install!
I've installed java by this method on all my five boxes running ubuntu, 2 x xubuntu and 2 x lubuntu without any problems whatsoever and they all continue to update to the latest java versions without problems.

oracle-java7-installer is just a script to download the java package from oracle and install it to a temporary tar.gz. It will then unpack that file and install java and during that install it will put up an acceptance of license terms window which you must accept to continue.

With your break in internet access it may have corrupted the package or missed some files and my best suggestion is to rerun sudo -apt-get update and try again. If that fails go to the webupd8 link and read the full page, you may need to uninstall and reinstall the oracle-java7-installer if that has been corrupted!

---

### Post by majorburt on 2012-10-26
> **lightning slinger said:**
> Not sure what's gone wrong with your install!
I've installed java by this method on all my five boxes running ubuntu, 2 x xubuntu and 2 x lubuntu without any problems whatsoever and they all continue to update to the latest java versions without problems.

oracle-java7-installer is just a script to download the java package from oracle and install it to a temporary tar.gz. It will then unpack that file and install java and during that install it will put up an acceptance of license terms window which you must accept to continue.

With your break in internet access it may have corrupted the package or missed some files and my best suggestion is to rerun sudo -apt-get update and try again. If that fails go to the webupd8 link and read the full page, you may need to uninstall and reinstall the oracle-java7-installer if that has been corrupted!

finally got the thing installed!!!!! i used the terminal again and i guess it took this time. 

thanks for all the help everyone!!!

---

