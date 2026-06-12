---
title: "VLC media player"
date: 2005-07-12
forum: General Help
---

### Post by blu.gecko on 2005-07-12
Im no pro, but when I tried installing vlc 0.8.1 It told me I needed another package, when I installed that package it told me i needed 10 other packages, anyone have the simplified version?

It seems like every video player has 20 thousand deps you have to install......kinda a pain in my !@#$

---

### Post by dave9191 on 2005-07-12
How are you trying to install it? If you use "sudo apt-get install vlc" it will install the player and any missing dependancies for you. 

Dave

---

### Post by blu.gecko on 2005-07-12
I tried that I got a message, something to do with the drive e.....cant remember
 :-?

---

### Post by ssck on 2005-07-12
[QUOTE=blu.gecko]I tried that I got a message, something to do with the drive e.....cant remember
 :-?[/QUOTE]


you should be able to find vlc in synaptics package manager.it will install all dependencies for you as well.

---

### Post by blu.gecko on 2005-07-12
root@ubuntu:/home/blu # sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc
root@ubuntu:/home/blu #

According to [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=VLC&searchon=names&subword=1&version=hoary&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=VLC&searchon=names&subword=1&version=hoary&release=all)

there are 23 packages to download and install

---

### Post by yanik on 2005-07-12
*sudo apt-get install vlc* worked for me

---

### Post by kleeman on 2005-07-12
Do you have universe enabled in /etc/apt/sources.list  ???

---

### Post by blu.gecko on 2005-07-12
Eh? universe in what?

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by kleeman on 2005-07-12
Try this:
sudo gedit /etc/apt/sources.list

look for a line near the top like

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main 

and change it to

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

(and the next one as well - you get the idea)
this adds the universe, restricted and multiverse file repositories

vlc is in universe

save and then
sudo apt-get update
sudo apt-get install vlc

---

### Post by bgstratt on 2005-07-12
your best bet is to go to [www.ubuntuguide.org](www.ubuntuguide.org) and once there, click on the link which details how to enable extra repositories.  You may have to scroll down a little bit to get to that particular section though.  Actually, better yet, here is my sources.list file, just save it and copy it to /etc/apt/sources.list.  To do that, open a terminal window, i.e. applications, then system, then terminal.  Once it is open, change to the directory  where the file is saved, most likely the desktop, so type "cd Desktop" make sure to use the capital D in desktop.  After that, type "sudo mv sources.list.txt /etc/apt/sources.list"  Please omit the quotes, you don't need them.  Once you have completed that, please type "sudo apt-get update" then you can go into synaptic, or just type "sudo apt-get install vlc"  This should get rid of any missing files, or dependency problems.

---

### Post by blu.gecko on 2005-07-12
ehh did I do this right? 

root@ubuntu:/home/blu # sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release [26.2kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages [490kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages [2169kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages [88.4kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages [490kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources [175kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources [1320B]
99% [11 Packages bzip2 0]                                            150kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
  Sub-process bzip2 returned an error code (2)
Fetched 2992kB in 18s (162kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/home/blu #

---

### Post by blu.gecko on 2005-07-12
Thanks Guys....got it working!

---

### Post by kleeman on 2005-07-12
Maybe just a network problem. Retry "sudo apt-get update"
and just in case post your /etc/apt/sources.list file

---

### Post by blu.gecko on 2005-07-12
only known issue at this time is I cant hear mp3 songs......

---

### Post by kleeman on 2005-07-13
Try installing libmad0

---

### Post by blu.gecko on 2005-07-13
Well, still no luck with VLC altho I did a apt-get install xine-ui and everything worked, I didnt try dvd's yet. It even played mp3's...big bonus :-)

---

