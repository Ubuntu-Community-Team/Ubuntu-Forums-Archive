---
title: "Trying to write a little script to install all my software"
date: 2012-10-30
forum: General Help
---

### Post by Kruger2147 on 2012-10-30
Hey, so my computer sucks, and little things go wrong so I end up reformatting it all the time. I'm also of a little fickle so I end up installing different OS's on my laptop (all ubuntu o
r linux mint), and it gets kind of annoying having to go and find ppa's and install everything one by one, so I'm trying to make a little script or executable text document and was hoping to get some help writing it. Here's what I have so far:

[PHP]sudo add-apt-repository ppa:kevin-mehall/pithos-daily && sudo add-apt-repository ppa:videolan/stable-daily && sudo add-apt-repository ppa:webupd8team/y-ppa-manager && sudo add-apt-repository ppa:skype-wrapper/ppa && sudo add-apt-repository ppa:transmissionbt/ppa && sudo add-apt-repository ppa:pidgin-developers/ppa && sudo add-apt-repository ppa:libreoffice/ppa && sudo apt-get update && sudo apt-get install pithos vlc y-ppa-manager skype-wrapper transmission pidgin libreoffice gnome-do && sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove && sudo apt-get autoclean[/PHP]I was also wondering how I would fit the insallation of Spotify for Linux in. Here's the instuctions from their website:

**Debian**
 # 1. Add this line to your list of repositories by editing your [FONT=Courier New]/etc/apt/sources.list deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free  [/FONT]
# 2. If you want to verify the downloaded packages, you will need to add our public key [FONT=Courier New]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59[/FONT]  
# 3. Run apt-get update sudo apt-get update  
# 4. Install spotify! [FONT=Courier New]sudo apt-get install spotify-client[/FONT]


How would I go about setting all this up so I can just click on a file and have it open a terminal and start running and installing everything?

---

### Post by jerrrys on 2012-10-30
I would think that one of the standard backup methods would work as long as it appears in software sources list.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+software&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+software&as_qdr=all&sa=Google+Search&lang=en)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

---

### Post by oldfred on 2012-10-30
I did something similar as I install to two computers and every 6 months with multiple installs of the next version.

All I did was run the command from command line and then list history. Then copied history to bash file. Of course I had a lot of typos errors in my command line, but it let me test & verify which lines really worked.

I wanted to find some checking and add some distribution based variables. You then can add whatever works.

```
#!/usr/bin/env bash -x
# -x adds debugging mode set +x or set -x

# Repositoires - Normally users have the first 4 enabled - main, universe, multiverse, restricted
# Check if we are on Ubuntu
if [ "$(lsb_release -is)" != "Ubuntu" ] ; then
    echo "This script is only intended to run on Ubuntu"
    exit 255
fi

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi

# Get distro
distro=$(lsb_release -cs)

src=/etc/apt/sources.list
#save your original sources.list file.
echo "Backing Up The sources.list"
cp -i /etc/apt/sources.list /etc/apt/sources.list_backup
#this updates everything
apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade



```

---

### Post by Vaphell on 2012-10-30
spotify
[http://www.liberiangeek.net/2012/04/the-quickest-way-to-install-spotify-client-in-ubuntu-12-04-precise-pangolin](http://www.liberiangeek.net/2012/04/the-quickest-way-to-install-spotify-client-in-ubuntu-12-04-precise-pangolin)
simply copy-paste those lines into your script.

Btw, if you don't want the script to fail in case of a single operation going wrong
(missing repository or whatever) you should split that chain of commands glued together with &&

```
#!/bin/bash

# Check if we are root
if [ $UID -ne 0 ]
then
    echo "Please run this as root!"
    exit 255
fi

# PPAs one by one
add-apt-repository ppa:kevin-mehall/pithos-daily
add-apt-repository ppa:videolan/stable-daily
add-apt-repository ppa:webupd8team/y-ppa-manager
add-apt-repository ppa:skype-wrapper/ppa
add-apt-repository ppa:transmissionbt/ppa
add-apt-repository ppa:pidgin-developers/ppa
add-apt-repository ppa:libreoffice/ppa
# spotify, avoid duplicates in sources.list
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
grep -q spotify /etc/apt/sources.list || sh -c 'echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list'

apt-get update && apt-get install pithos vlc y-ppa-manager skype-wrapper transmission pidgin libreoffice gnome-do spotify-client-qt

apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove && sudo apt-get autoclean  

```

---

### Post by Kruger2147 on 2012-10-30
Awesome thank you for that, one last questions, how do I save it so I can click and run it? 

I tried saving it as a normal text document, then giving it permission to be an executable, but when i select "run in terminal" or just "run" noting happens.

---

### Post by oldfred on 2012-10-30
Better to use terminal, cd to folder with script,  and run with sudo from that. Then if you get any messages you can see them.

---

