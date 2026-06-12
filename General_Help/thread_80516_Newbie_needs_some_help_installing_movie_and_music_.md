---
title: "Newbie needs some help installing movie and music players"
date: 2005-10-22
forum: General Help
---

### Post by karishbhr on 2005-10-22
Ok, I have a few very Newbie questions... I need step by step answers please.

1. I need a movie player, everyone tells me mplayer, I downloaded it and tried to install it with the config files and I got this error:

> karishbhr@BlakesPC:~$ /home/karishbhr/Desktop/MPlayer-20050806/configure
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... not found
Checking for gcc version ... not found
Checking for gcc-3.4 version ... 3.4.5, ok
Checking for host cc ... gcc-3.4
Checking for CPU vendor ... AuthenticAMD (6:10:0)
Checking for CPU type ...  Unknown CPU Type
Checking for GCC & CPU optimization abilities ... Your gcc-3.4 does not even support "i386" for '-march' and '-mtune'.
error
Checking for kernel support of mmx ... failed
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmx2 ... failed
It seems that your kernel does not correctly support mmx2.
To use mmx2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnow ... failed
It seems that your kernel does not correctly support 3dnow.
To use 3dnow extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnowex ... failed
It seems that your kernel does not correctly support 3dnowex.
To use 3dnowex extensions in MPlayer, you have to upgrade/recompile your kernel!Checking for kernel support of sse ... failed
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... no
grep: libavcodec/allcodecs.c: No such file or directory
Checking for assembler (as 2.16.1) ... ok
Checking for Linux kernel version ... 2.6.12-9-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... no
Checking for i18n ... no
Checking for langinfo ... no
Checking for language ...
Error: help/help_mp-en.h not found

Check "configure.log" if you do not understand why it failed.


2. How do I install deb packages? I get invalid archive when I try to launch them

3. What is a good itunes alternative for Linux (good library, exc.)

4. I need some very very extensive and easy to understand guides for ubuntu

---

### Post by jasmuz on 2005-10-22
Hi!

First off, you can get Mplayer off the Ubuntu repositories.
To install DEB files, open a terminal and type sudo dpkg -i packagename.deb
A good replacement for Itunes (not necesarily for Ipod) is Muine.

For guides on how to work Ubuntu out, check this:
[https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")
[http://www.ubuntuforums.org/showthread.php?t=53050]("http://www.ubuntuforums.org/showthread.php?t=53050")

Hope this helps.
Take care!

---

### Post by Dr. Nick on 2005-10-22
Trying to compile files from a tar.gz needs build-essential package. It can be installed using synaptic. Also mplayer is in synaptic as mentioned previously and will be mainly automated installation process. 

amaroK is a powerfull media player also avaible from synaptic or ```
sudo apt-get install amaroK
``` from a terminal. amaroK requires alot of extra packages since it wasnt built for gnome but their are lots of other choices in players aswell.

Go to System->Help for some guides and also cruise over to the howto forums for more guides

---

### Post by mcpish on 2005-10-22
personally I'd recommend VLC as your media player.

---

### Post by cbudden on 2005-10-22
I like rythmbox as my music player, and either mplayer or VLC for movies.

---

### Post by Plank117 on 2005-10-22
One thing you're going to want to do is get the win32 codecs. That's really the only way you'll be able to play even close to half of the video files on the internet. 
```
sudo apt-get install win32codecs
```
You'll probably need to add some other repositories (can't remember which ones). I think I got this package off of either the multiverse or backports.

---

### Post by karishbhr on 2005-10-22
it said it coudlnt find the package

---

### Post by BatsotO on 2005-10-22
mplayer is kind of hardware specific, for intel base and amd base processor.  You can    find it and install it via synaptic if you want the GUI mode, or that apt-get if you know the exact name of the packace.

I think you just picked up wrong version for your cpu ( that   Detected host architecture: i386 thing and Checking for CPU vendor ... AuthenticAMD (6:10:0) ), if i'm not mistaken, you try to install install base mplayer on a AMD machine.

as for other media player, i use xine for video and xmms for audio, they can run mp3  and mpg file with help of gstreamer  ( they all can be found in synaptic ).

for guide to ubuntu, i think here is the place.

good luck

---

### Post by karishbhr on 2005-10-22
I know RPM isnt for ubuntu, but is there a way I can install them?

How do I make streaming stuff use VLC  like gamespot.com videos or something like that (now that I installed it)?

Here is what happens when I try to install mplayer > karishbhr@BlakesPC:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  aalib1 gcc-3.3-base libdirectfb-0.9-20 libfaad2-0 libstdc++5 libungif4g
  libxvidcore4 slang1 xmms
Suggested packages:
  w32codecs libdvdcss mplayer-doc
Recommended packages:
  mplayer-fonts libmikmod2 xlibmesa-gl libgl1
The following NEW packages will be installed:
  aalib1 gcc-3.3-base libdirectfb-0.9-20 libfaad2-0 libstdc++5 libungif4g
  libxvidcore4 mplayer-386 slang1 xmms
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 5759kB/6204kB of archives.
After unpacking 19.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
karishbhr@BlakesPC:~$


The same error is happening every time I try to install something!

---

### Post by Dr. Nick on 2005-10-22
Dont push "Y" if you are, just try to hit enter


To install an rpm file you need a package called alien. Im not sure the exact commands to use it as their is usually a .deb file for most packages also

---

### Post by BatsotO on 2005-10-23
have you try synaptic?

i'm a newbie too and i found synaptic is a great help for me to find the right packages and installing them compared to apt-get. 
Basicly they are the same aplication, ubuntu can't run apt-get and synapticat the same time because they do exactly the same thing, but with synaptic we can search for apt that we need, have a look at what it does ( so we can learn a bit ), and when we done searching and selecting we can leave the rest to the machine. It works for me everytime.

just curious, what processor you have? Because from your previuos post it stated that cpu vendor was AMD, and from your newer post you install mplayer for intel cpu.
Some apt, like mplayer, were built for specific processor. I found a number of different mplayer for intel and AMD in synaptic, and I'm sure they are not RPMs. Why bother installing RPM on debian base distro when you can find the DEB ( not the latest release maybe... ), and if there's no DEB available, try tar.gz.

---

