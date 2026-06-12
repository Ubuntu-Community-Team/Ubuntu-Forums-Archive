---
title: "Java 6 Installation"
date: 2017-12-29
forum: General Help
---

### Post by kan1969 on 2017-12-29
Hello All,

I am in a position to install Java 6 JDK in my Ubuntu that I have installed in Virtualbox. I need this for a scenario. I do not know how to install it and set path, environment variables to it.

Kindly guide me and give me installation steps to it.

Thanks,
With Kind Regards,
Kannan

---

### Post by QIII on 2017-12-29
Hello!

Java 6 is discontinued and it is riddled with security issues.

Are you absolutely sure you need it?

---

### Post by kan1969 on 2017-12-29
Hello,

Yes, I need it and have downloaded the binary files from Oracle Java Website.

Thanks,
Kannan

---

### Post by dragonfly41 on 2017-12-29
This link refers to Java 6 required for Android Studio ..

[https://github.com/uw-it-aca/spacescout-android/wiki/1.-Setting-Up-Android-Studio-on-Ubuntu](https://github.com/uw-it-aca/spacescout-android/wiki/1.-Setting-Up-Android-Studio-on-Ubuntu)

---

### Post by kan1969 on 2017-12-30
Hello All,

I tried to go with that link: "[https://github.com/uw-it-aca/spacesc...udio-on-Ubuntu]("https://github.com/uw-it-aca/spacescout-android/wiki/1.-Setting-Up-Android-Studio-on-Ubuntu")", but that returned with an error given below.

```


sudo apt-get install openjdk-6-jdk-headless
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'playonlinux.lis' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package openjdk-6-jdk-headless

```

Thanks,
Kannan

---

### Post by dragonfly41 on 2017-12-30
I found this suggestion .. using PPA
```
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt update
sudo apt install openjdk-6-jdk
```

You will need to dig around to find java 6 archives.

[Later addition]

I see in Synaptic Package Manager in my Ubuntu 16.04 there is also oracle-java6-installer

[https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get)

---

### Post by deggen2 on 2018-02-01
Have anyone solved this problem?
I also need java 6 for my work. I created dual boot just for this work and installed ubuntu 16.04.

sudo apt-get install openjdk-6-jre

"The following packages have unmet dependencies: openjdk-6-jdk : Depends: openjdk-6-jre (= 6b38-1.13.10-1)                 Recommends: libxt-dev but it is not going to be installed openjdk-6-jre : Depends: openjdk-6-jre-headless (= 6b41-1.13.13-0ubuntu0.14.04.1)                 Depends: libgif4 (>= 4.1.4) but it is not installable                 Depends: libatk-wrapper-java-jni (>= 0.30.4-0ubuntu2) but it is not going to be installed                 Recommends: icedtea-netx but it is not going to be installed openjdk-8-jre-headless : Breaks: tzdata-java but 2016c-0ubuntu1 is to be installed                          Breaks: tzdata-java:i386"

returns a lot of dependency errors. 

I have tried to install each one mentioned but there are still errors. I am willing to change to any version of ubuntu to solve this problem. thanks!

---

### Post by QIII on 2018-02-01
Hello!

If your employer requires it, have they been able to advise you with regard to how to install it?

I can't find Oracle Java 6 on Oracle's website (not surprising since they have discontinued it).  The only place one can legally get Oracle Java is from Oracle itself.  They do not allow anyone else to distribute the binaries. 

According to [OpenJDK's instructions]("http://openjdk.java.net/install/") for installing OpenJDK 6 on Debian/Ubuntu:

```
sudo apt-get install openjdk-6-jre
```

If the package or its dependencies are not available in the repo, it's not there.  If you are getting dependency errors, it's likely that nobody is maintaining the package any longer.

I'm a member of the ODN and even so I have to say that using Java 6 is irresponsible to the point of foolish.  Java 6 is, in large part, responsible for what I call the October of Java Exploits several years ago.  That event is what caused Oracle to immediately drop support for Java 6.  I could not, in good conscience, help you install it even if I could find it.

Were I you, I would have an earnest discussion with your employer.  But I've been doing this computer thing for over 40 years, so I have some expertise.  I own my own company and would turn down a contract if the client wanted to use Java 6.  Flat out walk away.  

But if your employer requires it, they should be able to help you find and install it.  They've placed you in a tough spot.

---

