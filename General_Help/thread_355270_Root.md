---
title: "Root?"
date: 2007-02-07
forum: General Help
---

### Post by bluestatic_91 on 2007-02-07
I need java installed. I downloaded the jre-6-linux-i586.rpm.bin and I cannot seem to open it. According to [http://www.wikihow.com/Install-Java-on-Linux](http://www.wikihow.com/Install-Java-on-Linux) , I need to "login as root". that's where I get hung up. I dunno how I login as root. Please help asap. I need java for practically every site in the world.

---

### Post by bodhi.zazen on 2007-02-07
Ubuntu uses sudo

Try : ```
sudo -i
```

When asked for a password enter your log in password p

---

### Post by ~LoKe on 2007-02-07
You don't want RPM's, you want .bin's or .deb's.

But, either way, to become root, you could just use sudo:
```
sudo <command>
```
eg.
```
sudo sh file.bin
```
Or
```
sudo su
```

---

### Post by 23meg on 2007-02-07
Follow these instructions to install Java: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by aysiu on 2007-02-07
RPM files should be a last resort.

Read this instead:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

There's never any reason to log in as root in Ubuntu.

---

### Post by neilp85 on 2007-02-07
You shouldn't be trying to install an rpm on ubuntu since it is debian based. You should use the version in the repos.
```
sudo apt-get install sun-java6-jre
```

---

### Post by bluestatic_91 on 2007-02-07
Okay, I am root now, but I can't get java still. I tryed all of the commands, but it keeps saying either "no such file or directory", or "E: invalid operation" I also tryed doing it the easy way through add/remove applications search, and no results when I search.

---

### Post by Maestro23 on 2007-02-07
> **bluestatic_91 said:**
> Okay, I am root now, but I can't get java still. I tryed all of the commands, but it keeps saying either "no such file or directory", or "E: invalid operation" I also tryed doing it the easy way through add/remove applications search, and no results when I search.

Can you post your /etc/apt/sources.list

#cat /etc/apt/sources.list

---

### Post by bodhi.zazen on 2007-02-07
You likely need to enable a few repositories :

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then : ```
sudo aptitude update
``` and re-try installing java :p

---

