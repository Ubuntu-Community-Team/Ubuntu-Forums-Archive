---
title: "Problems with apt-get update"
date: 2020-08-15
forum: General Help
---

### Post by mikes365 on 2020-08-15
So today I just downloaded Ubuntu 20.04 and I am also a complete noob everything is going quite well...

But then I ran into a problem while running the "sudo apt-get update" command...This is the output:

gn:1 cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal InRelease
Err:2 cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) focal InRelease   
Hit:4 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:5 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) focal-backports InRelease         
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [107 kB]   
Reading package lists... Done      
E: The repository 'cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by mikes365 on 2020-08-15
Please Help me !?

---

### Post by deadflowr on 2020-08-15
```
sudo apt edit-sources
```
add a # symbol to the front of the line that starts with
deb cdrom.
Save and exit and rerun the update command.

---

### Post by CelticWarrior on 2020-08-15
Or open Software & Updates then either in the first or the second tab untick or remove the CD-ROM entry.

---

### Post by mikes365 on 2020-08-15
Thank you legend

---

### Post by TheFu on 2020-08-15
Something didn't complete in the install. The sources pointing at the local media should have been cleaned up during the install and left pointing at local mirrors for your country. 

I've never seen this problem before on any system with a working internet connection.

Usually, for systems that are off-line, never connected to the network, we have to go and set this up to only use local sources.

---

### Post by mikes365 on 2020-08-15
Yeah but I have had problems with my router today, for some reason my internet slows down like ALLOT, but it went back to normal about 5 minutes ago...Could that be it ?

---

### Post by TheFu on 2020-08-15
> **mikes365 said:**
> Yeah but I have had problems with my router today, for some reason my internet slows down like ALLOT, but it went back to normal about 5 minutes ago...Could that be it ?

99% not.  There are specific settings to control where updates are allowed to come from.  Local files usually are used only during installation.

CelticWarrior and deadflowr have 2 different methods to accomplish the same thing above. Just depends on which method you'd prefer or find first.

---

### Post by QIII on 2020-08-15
Just as an aside, mikes365:

When you post a query for help, we understand you would like an answer as quickly as possible.  But you need to bear in mind that everyone here, including the Staff and Admins, are all volunteers giving our time as we have it.  Everyone has a life outside of this forum, and the forum's populace is scattered all over the Earth.  That means that your question may not be seen immediately by the person who has the very best answer for you.

So please don't post and impatiently post again minutes later.  That is less likely to bring you help sooner than it is to drive people away from someone who appears to be impatient and demanding.

If you don't get an answer in about 12 hours, feel free to bump your post to get it in front of a different set of members.

Thanks!

---

### Post by masoodaslami on 2021-01-31
Thank you so much! You saved my day.

---

### Post by omidrayaneh on 2021-12-17
thanks =d>=d>=d>

---

### Post by omidrayaneh on 2021-12-17
> **CelticWarrior said:**
> Or open Software & Updates then either in the first or the second tab untick or remove the CD-ROM entry.
thanks very much=d>=d>

---

### Post by coffeecat on 2021-12-17
Ancient thread - closed.

---

