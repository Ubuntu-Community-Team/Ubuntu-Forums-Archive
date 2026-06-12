---
title: "Problems with apt"
date: 2005-06-15
forum: General Help
---

### Post by Monzilla on 2005-06-15
I get this message when I try apt-get install, apt-get update and apt-get upgrade.

W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by netrattler on 2005-06-15
Could your post a copy of your /etc/apt/sources.list and I'll see if I can figure it out.

Joe

---

### Post by SGC on 2005-06-15
[QUOTE=Monzilla]I get this message when I try apt-get install, apt-get update and apt-get upgrade.

W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems[/QUOTE]
 I have this problem a few days ago, here is how I fix it:

- Open */etc/apt/sources.list*  and remove the the line that starts with *deb cdrom...*
- Do *apt-get update*
- Open synaptic and go to edit > add CD-ROM
- Insert ubuntu or kubuntu cd and click ok

---

### Post by Monzilla on 2005-06-15
sources.list

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by mtron on 2005-06-15
replace the file sources.list with [this](http://ubuntuguide.org/index.html#extrarepositories) 

and it will work.

The error was due to the hoary install CDROM in your sources file, so when you update your sources, and do not have the install cd in the drive, it will display this error. You can just remove this line from the file, or follow the link above.

Cheers mtron

---

### Post by mtron on 2005-06-15
just delete 
"deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted"

and save the file.

then run sudo apt-get update

---

### Post by Monzilla on 2005-06-15
[QUOTE=SGC]I have this problem a few days ago, here is how I fix it:

- Open */etc/apt/sources.list*  and remove the the line that starts with *deb cdrom...*
- Do *apt-get update*
- Open synaptic and go to edit > add CD-ROM
- Insert ubuntu or kubuntu cd and click ok[/QUOTE]
 I can't open synaptic, it won't let me. I get an error saying I need to open it as the root user, and I am the root user.

---

### Post by netrattler on 2005-06-15
Put your Hoary cd in and then do sudo apt-get update and sudo apt-get upgrade because it looks like it is trying to install something from the CD. your sources.list is exactly like mine so you shouldn't have any more problems after this.

Joe

---

### Post by az on 2005-06-15
Are you on the internet when you try?  Is your connection properly set up?

---

### Post by SGC on 2005-06-15
[QUOTE=Monzilla]I can't open synaptic, it won't let me. I get an error saying I need to open it as the root user, and I am the root user.[/QUOTE]
 Ok, instead of adding the cd in synaptic add it from the terminal using the following command:

```
apt-cdrom add
```

after that do *apt-get update* and that should fix the problem

---

