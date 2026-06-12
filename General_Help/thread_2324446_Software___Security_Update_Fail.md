---
title: "Software  / Security Update Fail"
date: 2016-05-13
forum: General Help
---

### Post by anon24 on 2016-05-13
Running 16.04

I am trying to update because I keep getting a notification saying that I need to. When I try, it says, "Failed to download repository information". I try through the Terminal and it says something similar.

```
~$ sudo apt-get update
[sudo] password for x: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [93.3 kB]    
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Ign:7 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial InRelease   
Hit:8 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Ign:9 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial Release
Ign:10 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
Ign:11 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en_US
Ign:14 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en
Ign:15 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main DEP-11 64x64 Icons
Ign:10 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
Ign:11 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en_US
Ign:14 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en
Ign:15 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main DEP-11 64x64 Icons
Ign:10 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
Ign:11 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en_US
Ign:14 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en
Ign:15 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main DEP-11 64x64 Icons
Ign:10 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
Ign:11 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en_US
Ign:14 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en
Ign:15 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main DEP-11 64x64 Icons
Ign:10 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
Ign:11 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en_US
Ign:14 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en
Ign:15 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main DEP-11 64x64 Icons
Err:10 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
  404  Not Found
Err:11 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
  404  Not Found
Ign:12 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en_US
Ign:14 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main Translation-en
Ign:15 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main DEP-11 64x64 Icons
Fetched 93.3 kB in 8s (10.9 kB/s)                                              
Reading package lists... Done
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
W: The repository 'http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by grahammechanical on 2016-05-13
Disable the PPA.

System Settings>Software & Updates>Other Software

Regards.

---

### Post by anon24 on 2016-05-14
Woot, that worked! Thank you!

---

### Post by jordan-lux on 2017-01-01
Ok. So sorry to revive a solved thread, but there is a way to fix it so that it works properly and you don't happen to miss any updates from it. (I know the developer has not released anything new to his website in a long time but still.)

So all that you need to do is re-add the PPA in one of two ways.

You can first use:

sudo add-apt-repository ppa:colingille/freshlight
sudo apt-get update

Second way: (the way that I did it and for sure works)

sudo su
add-apt-repository ppa:colingille/freshlight
apt-get update

I used root user to add it because even though sudo gives super user powers root controls the whole system and so it stands to reason that it should be used to fix a system issue like this. Especially when it crashes the software updater.

---

### Post by vasa1 on 2017-01-01
> **jordan-lux said:**
> ...
I used root user to add it because even though sudo gives super user powers root controls the whole system and so _it stands to reason that it should be used to fix a system issue like this_. Especially when it crashes the software updater.
??? Seems very unusual advice :(

---

### Post by jordan-lux on 2017-01-02
> **vasa1 said:**
> ??? Seems very unusual advice :(

Why do you say that? Sudo does give you "nearly" root access but not full root access. I also gave the non root way but my preference is root.

---

### Post by coffeecat on 2017-01-02
> **jordan-lux said:**
> even though sudo gives super user powers root controls the whole system and so it stands to reason that it should be used to fix a system issue like this.

No "stands to reason" about it at all. I haven't used a root shell for a long time. You might benefit from reading this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also, you might wish to acquaint yourself with what is said there about the potential disadvantages of "sudo su" as opposed to "sudo -i"- derived from this: [https://ubuntuforums.org/showthread.php?t=983645&p=6188826#post6188826](https://ubuntuforums.org/showthread.php?t=983645&p=6188826#post6188826)

---

### Post by RobGoss on 2017-01-02
> **grahammechanical said:**
> Disable the PPA.

System Settings>Software & Updates>Other Software

Regards.


**+1** grahammechanical suggestion

---

### Post by cod3r- on 2017-12-28
And how will this happen in a server version ..?


```


root@softinfo:~# apt-get update
Hit:1 [http://repo.ajenti.org/debian](http://repo.ajenti.org/debian) main InRelease
Hit:2 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) xenial InRelease
Ign:3 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial InRelease
Ign:4 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial Release
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Err:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
  **404  Not Found**
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Hit:9 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:10 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial-security InRelease
Hit:11 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:12 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial-proposed InRelease
Hit:13 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  **404  Not Found**
E: Some index files failed to download. They have been ignored, or old ones used instead.
root@softinfo:~# sudo systemctl restart salt-minion





```

---

### Post by coffeecat on 2017-12-28
@cod3r-, this is an old thread, long ago marked solved, and already necromanced once before. You will not get help posting to it. If you need help, please start your own thread.

Back to sleep, ancient thread. Thread closed.

---

