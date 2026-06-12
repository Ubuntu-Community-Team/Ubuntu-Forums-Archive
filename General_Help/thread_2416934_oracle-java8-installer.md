---
title: "oracle-java8-installer"
date: 2019-04-18
forum: General Help
---

### Post by thecloud9 on 2019-04-18
This seems to be a recurring issue. Solutions come and go, yet I have found no known solutions out there.

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer

same with:
cho "deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main" | sudo tee /etc/apt/sources.list.d/webupd8team-java.list 
echo "deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main" | sudo tee -a /etc/apt/sources.list.d/webupd8team-java.list 
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886 
sudo apt-get update 
sudo apt-get install oracle-java8-installer

returns following errors: 

Connecting to download.oracle.com (download.oracle.com)|184.27.222.134|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
2019-04-18 02:06:35 ERROR 404: Not Found.


download failed
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java8-installer

---

### Post by logix2 on 2019-04-18
Oracle changed the license recently and now it's required logging in using an Oracle account to download Oracle Java versions older than 12. That makes it impossible for the installer to work any more (as far as I understand). Do you specifically need Oracle Java? With the new license, it's available at no cost only for personal and development use, requiring a commercial license for other cases. You could use the Ubuntu OpenJDK packages instead, or use the [Zulu OpenJDK]("https://www.linuxuprising.com/2019/04/install-latest-openjdk-12-11-or-8-in.html") builds which are up to date, you can install any version you want (12, 11, 8 and even 7), and are free and open source software.  There's also [AdoptOpenJDK]("https://adoptopenjdk.net/"), but you'll have to install it manually.

---

