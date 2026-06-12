---
title: "This is very frustrating. JDK help"
date: 2012-12-02
forum: General Help
---

### Post by imfree19 on 2012-12-02
Hi everyone. Ive been having difficulty trying to setup a java jdk environment. Im having all kinds of trouble with it and I keep getting different errors. At first I tried to install webstorm and then it said I needed a jdk environment. So I tried to install sun java jdk 7 and this is what Im getting


/usr/local/jdk1.7.0_07//bin/java: 1: /usr/local/jdk1.7.0_07//bin/java: Syntax error: end of file unexpected (expecting ")")

Anybody have any ideas?

---

### Post by QIII on 2012-12-02
How did you try to install it?  

I suspect your method was either dated or wrong, since Oracle Java is beyond Update 7.

---

### Post by imfree19 on 2012-12-02
[http://www.oracle.com/technetwork/java/javase/downloads/jdk7u7-downloads-1836413.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7u7-downloads-1836413.html)

I think 7 is the latest jdk environment. I installed it to usr/local

---

### Post by QIII on 2012-12-02
It's at u9, I believe and there is a snapshot of u10.

The very easiest way to get the whole thing, JRE, JDK and plugin, is to see the Java wiki link in my signature, find "Oracle Java 7", then "Command line methods" and then the link "Using webupd8.org's strikingly simple method".

The PPA is trustworthy and webupd8 keeps it up to date so Oracle Java is updated as Oracle releases.  All you have to do is your normal Ubuntu updates.

---

### Post by imfree19 on 2012-12-02
Ok I tried that method and it wont even let me get the repository. This is what happens 


sudo add-apt-repository ppa:webup8team/java
Cannot access PPA ([https://launchpad.net/api/1.0/~webup8team/+archive/java](https://launchpad.net/api/1.0/~webup8team/+archive/java)) to get PPA information, please check your internet connection.

My internet connection is fine

---

### Post by imfree19 on 2012-12-02
Nevermind I realized i typed it in wrong. My bad

---

### Post by imfree19 on 2012-12-02
Now this is what is really irritating me. This happened when I tried to install it myself too. When I check to see what version of java I have, it comes up with this...

~$ java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

I did everything that the method told me to do

---

### Post by QIII on 2012-12-02
Just to be sure...


```
sudo add-apt-repository ppa:webupd8team/java 
sudo apt-get update 
sudo apt-get install oracle-java7-installer
```

Did you run each command separately?

What happened at each of those commands?

Did you get any errors when you updated?

How about when you installed?

You can retry the second and third commands if you want to see for sure.

---

### Post by imfree19 on 2012-12-02
I did not get any errors and it seemed like it worked perfectly until I checked the version. I tried those last two commands again and it didnt change anything

This is what happened when I tried update-java-alternatives

sudo update-java-alternatives -l
java-1.6.0-openjdk-i386 1061 /usr/lib/jvm/java-1.6.0-openjdk-i386
java-1.7.0-openjdk-i386 1051 /usr/lib/jvm/java-1.7.0-openjdk-i386
java-7-oracle 1062 /usr/lib/jvm/java-7-oracle
kevin@kevin-Satellite-L745:~$ sudo update-java-alternatives -s java-7-oracle
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: alternative /usr/lib/jvm/java-7-oracle/jre/bin/jexec for jexec not registered, not setting.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.

---

### Post by imfree19 on 2012-12-03
Does anybody else have any advice?

---

### Post by slickymaster on 2012-12-03
Why don't you start from the beginning? A sort of a fresh installation.

Start by removing your previous jdk installation and all of it the dependencies.

Afterwards do this:

**_JRE7 installation_**
Type in the following commands then hit Enter after each.
```
sudo sh -c "echo 'deb http://www.duinsoft.nl/pkg debs all' >> /etc/apt/sources.list"
sudo apt-get update
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B2
sudo apt-get update
sudo apt-get install update-sun-jre
```

_**To install JDK 7**_
Type in the following commands then hit Enter after each.
```
cd /tmp
wget -c --no-cookies --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com" "http://goo.gl/g9cJl" -O jdk-7u7-nb-7_2-linux-i586-ml.sh
chmod +x jdk-7u7-nb-7_2-linux-i586-ml.sh
sudo sh jdk-7u7-nb-7_2-linux-i586-ml.sh
```

Then follow setup instructions without changing anything.

**_When the install is complete, use these commands_**

```
sudo mkdir -p /usr/lib/jvm/
sudo cp -R /usr/local/jdk1.7.0* /usr/lib/jvm/
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.7.0_07/bin/javac 1
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.7.0_07/bin/java 1
```

And that's it.

---

### Post by clement_De_Bigorre on 2013-08-18
Installing the oracle JDK: 
I had the same error message because downloaded the wrong file (yes newb).
 I was using the x64 jdk<version>.tar.gz file on 64 bit CPU machine but with a 32bit ubuntu installed.

I guess that's why the error is at the begining of the binary file. 

So, I replaced  the jdk by the i586 and it work as expected. Maybe it could help checking versions.

---

