---
title: "DVD mounting question and GUI installation on server"
date: 2013-10-04
forum: General Help
---

### Post by nrwahl-d on 2013-10-04
Hey, guys. For context: I'm fairly new to Linux (downloaded Ubuntu 12.04 desktop for my main computer about three weeks ago), so I'm only starting to learn the commands. And I've been hitting the forums with a barrage of questions. You've been amazingly helpful.

I'm running another computer offline as part of Bitcoin Armory... or I'm trying to. The Armory Offline Bundle, containing all necessary dependencies so that apt-get update is unnecessary, is only compatible up to 10.04. I wanted to put 10.04 on my offline computer to make running Armory easier, but it's been a battle. I couldn't find the desktop anywhere, only the server.

I installed the 10.04 LTS server and I've been trying to get a GUI on it while my cousin half-ass helps me via Facebook when he's not busy. I downloaded gnome-python-desktop-2.27.1.tar.gz, put it on a DVD, got /dev/sr0 mounted to /media/dvd, copied the .tar.gz file to /home/asdf/downloads, and decompressed it. Now the unzipped package is in /home/asdf.

My cousin told me to use:
'cd /home/asdf/gnome-python-desktop-2.27.1'
'./configure'
'make'
'sudo make install'

I don't know how accurate this is, but I never made it past './configure'. I get the following error message:

'configure: error: in '/home/asdf/gnome-python-desktop-2.27.1':
configure: error: no acceptable C compiler found in $PATH'

My cousin suggested I download build-essential, put it on a DVD, and copy/install it on the server.

I inserted the build-essential DVD. 'dmesg | grep dvd' shows that the DVD is sr0, and 'df' shows that /dev/sr0 is mounted on /media/dvd. However, when I enter 'ls -la /media/dvd', it shows the contents of the previous gnome-python-desktop-2.27.1 DVD. The build-essential DVD is nowhere to be found. I don't know if I should unmount and remount since it's 100% in use... basically, I'm completely confused and don't know what to do next. I need to get a GUI, any GUI really, added to this server. I like learning about the terminal but I don't want to have to depend on nothing but a server.

Even after I get a C compiler on the server I don't know what to do with it or where to put it.

Any help or links to forums that have answered this question will be greatly appreciated. Heh, I could finally get on with my life.

Due to the circumstances of my set-up I need a solution that doesn't require Internet use on my 10.04 computer. I'd like to install a GUI from a DVD, ideally.

P.S. My apologies if I come off as rambling. I'm trying to provide as much info as possible on where I am and what got me to this point.

---

### Post by enterdavertex on 2013-10-04
Try to install the build-essential with 
[B][U]sudo apt-get install build-essential
[/U][/B]This should be good.
****

---

