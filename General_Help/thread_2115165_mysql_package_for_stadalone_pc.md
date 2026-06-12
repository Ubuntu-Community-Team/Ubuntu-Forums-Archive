---
title: "mysql package for stadalone pc"
date: 2013-02-12
forum: General Help
---

### Post by Rakeshvijayan on 2013-02-12
Hi friend 

I have a few computer which have no Internet conneciton .But I need to install mysql and ubuntu updates  on every system ...

---

### Post by schragge on 2013-02-12
[apt-offline(8)]("http://manpages.ubuntu.com/manpages/precise/en/man8/apt-offline.8.html")

---

### Post by Rakeshvijayan on 2013-02-12
Thank schrags  but it have no clear how to Because  I am not a linux savvy  


I got some information about apt-offline package I dont know what its doing with 

[http://www.debian-administration.org/articles/648](http://www.debian-administration.org/articles/648)
>                                                                                    **Offline Package Management for APT**

         Posted by  [riteshsarraf]("http://www.debian-administration.org/users/riteshsarraf") on Sat 24 Oct 2009  at 14:43 

          Tags:   [apt]("http://www.debian-administration.org/tag/apt"),   [apt-offline]("http://www.debian-administration.org/tag/apt-offline")      
           This article is about Offline Package Management in Debian.   Debian is a pretty well known project. One of the things that makes  Debian very popular is APT (a.k.a Advanced Packaging Tool) which allows  remote package downloads, upgrades and dependency resolution.   Unfortunately it does require a network connection - unless you use apt-offline.
 In Debian, when you need to install a package, you usually would fire up the apt-get command and the software would just install without any hand holding.  
 While APT is really very cool one of the main reasons for its success  is the Debian Policy. The Debian Policy is like the brain of the  project that controls the entire project ensuring that all the bits and  pieces fit well together upto the Debian Standards. APT is just a result  of the fantastic Debian Policy work.
 In Debian, every package is very well self-contained and is tightly  related to each other using APT. APT does a very good job of integrating  and resolving dependencies for Package Management and takes off all the  Dependency Hell problems from the user.
 This is where the problem starts - for a machine which has network  access it works very well because APT generates the list of packages and  their dependencies and is able to download and install them  successfully.
 But when it comes to downloading a package individually on a  different machine, along wih resolving any dependencies this can be a  big problem.
 Consider this real world example:   I have a Debian box at home. At  home, I have no (or very slow/expensive dial-up) internet connection. At  work, I (or my friend) do have a very fast connection but (as part of  IT policy) am required to use Windows.
 I would still like to be able to painlessly update/upgrade my Debian box at home, with all the power and flexibility of APT.
 This is where apt-offline is useful.  [apt-offline]("http://apt-offline.alioth.debian.org/") is an *offline* APT Package Manager.
 Using apt-offline:
 
[LIST]
[*]You generate a signature on your Debian box at home and carry the  signature file on a removable medium (Probably a USB Stick).(e.g. "apt-offline set /tmp/apt-offline.txt")
[*]Now you take the USB Stick (with the apt-offline.txt signature file) to the office machine which could be running any linux version, or as I mentioned above, even Windows.
[*]There, you could run apt-offline giving it the signature file. (e.g. "apt-offline get C:\apt-offline.txt")
[*]apt-offline would generate you an archive file or a folder with all  the data. That data can be copied on a removable media. The removable  media can be attached back to the disconnected Debian box at home and  installed. (e.g. "apt-offline install /tmp/apt-offline.zip")
[/LIST]
 **Let's start with a 3 step  example**
 **Step 1**
 Generate a signature file on the Disconnected Debian box at home
 apt-offline set /tmp/apt-offline.sig  The above command will generate all information required from apt about updating its database.
 By default, with no additional arguments passed, apt-offline will extract information about **APT Package Database Update i.e. the --update option** as well as the list of **Packages to be upgraded i.e. the --upgrade option**. 
These options can also be individually passed if you want only one of those.
  **Step 2**
 Download data based on the signature file generated earlier
 apt-offline get C:\apt-offline.sig --threads 5  The above command will download data as mentioned in the signature  file. To speed up downloads (that can be from multiple apt  repositories), in this example we spawn 5 download threads.
 **Note:** It would be good to also download the bug reports for the packages that you are downloading.  So that example now becomes:
 apt-offline get C:\apt-offline.sig --bug-reports --threads 5  There are many more options that you can pass to apt-offline, like the --bundle option which would generate for you, an archive file with all the data.
 Once completed, you could just copy the data (an archive file, if you used the --bundle option) back to the removable medium and copy it back onto your offline host.
 **Step 3**
 Once you're back upon the home Debian machine, you feed the data from the removable medium to apt-offline:
 apt-offline install /media/USB/apt-offline.zip  This will update the APT database on your disconnected machine seamlessly.
 If there were packages that needed to be upgraded, now they would all  be available (with dependencies) in the APT database. So if you do an  apt-get upgrade now, APT won't prompt you mentioning even a single bye  download.  APT would find that all required packages are already present  in the APT  cache.
 I need to install mysql without net connection ,I think above how to give only create offline database of the  packages .its not give me how to install the packages in ubuntu box that have no net connection and any configuration in ubuntu box that need to install package 

Thanks for the great help

---

### Post by slickymaster on 2013-02-12
Take a look at this examples:

[Install MySQL without apt-get]("http://askubuntu.com/questions/29533/install-mysql-without-apt-get")
[How to install Mysql Server In Ubuntu Server that has no Internet Connection]("http://stackoverflow.com/questions/11789340/how-to-install-mysql-server-in-ubuntu-server-that-has-no-internet-connection")
[Offline MySQL installation (Using deb file and no internet connection)]("http://askubuntu.com/questions/221769/offline-mysql-installation-using-deb-file-and-no-internet-connection")

---

### Post by Rakeshvijayan on 2013-02-14
friends your suggestion were very highly things for me ...

I have 2 simple questions ?

1 ) Is it possible to install mysql, by manually  collecting whole .deb packages from /var/cache/apt/archives on mysql installed system to  ubuntu system have no Internet connection ..?

2) If i am using aptoncd in 12.04 do I need to have aptoncd on newly installed system for restore the package 


I am in trouble with this requirement

---

### Post by schragge on 2013-02-14
WRT your first question. I guess, after
```

sudo apt-get clean
sudo apt-get -d --reinstall install mysql-server

```
you'll get debs for *mysql* and all its dependencies in */var/cache/apt/archives*

---

### Post by Rakeshvijayan on 2013-02-14
> **schragge said:**
> WRT your first question. I guess, after
```

sudo apt-get clean
sudo apt-get -d --reinstall install mysql-server

```you'll get debs for *mysql* and all its dependencies in */var/cache/apt/archives*

Friend 

I need to install mysql on another system have no internet connection with deb package I already installed in my laptop .I Installed mysql in my laptop

---

### Post by slickymaster on 2013-02-14
Once you have the packages, either stick them in ```
/var/cache/apt/archives/
``` and run the standard ```
sudo apt-get install mysql-server
``` or simply cd into the directory where the packages are and run ```
sudo dpkg -i *.deb
```

---

### Post by schragge on 2013-02-14
> **Rakeshvijayan said:**
> I need to install mysql on another system have no internet connection with deb package I already installed in my laptop.Yes, I perfectly understand you. [color=green]sudo apt-get -d --reinstall install mysql-server[/color] won't reinstall mysql on your laptop, trust me. It will only download all needed debs into */var/cache/apt/archives*, nothing more.

[color=blue]**Update.**[/color]
Sorry, I was wrong. *apt-get -d --reinstall* won't download all dependencies recursively if you've already installed them before. To achieve this, do
```

sudo apt-get -d --reinstall install mysql-server `apt-cache --recurse -i depends mysql-server|awk '$2!~/^</{print$2}'|sort -u`

```

---

