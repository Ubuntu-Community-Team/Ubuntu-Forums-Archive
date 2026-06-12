---
title: "unable to load graphical interface."
date: 2007-09-08
forum: General Help
---

### Post by Mohdgame on 2007-09-08
I am new on Linux and I am having an annoying problem. From my shallow knowledge I say its from the graphic card driver, but I thought Geforce was compatible.

However, here is what happened. I installed my Ubuntu and it worked well, and it updated it self, however I went the Package Manager and searched for "gefroce" and downloaded 2 Geforce packages. But they think they were the same, they were "Geforce-glx" and "New gefroce-glx" if memory serves well. It worked well.

Then refresh rate if the screen was low, and it hurted my eyes. So I searched for something to fix it and then i clicked on "Screen effect" And it got me a message that i need to install the latest driver and Linux would download it for me. I was "Now i know whats wrong!" and clicked okay. Then it restarted and It got me this message.


This came up on the screen: I got this message from an old post on this forum. The only difference is the date. 

> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revison 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP
Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice,
(II) informatonal, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Logfile: "/var/log/Xorg.0.log"
(==) Using config file: "/etc/X1/Xorg.conf" 

Should I reinstall ubuntu? Though, I heared that i was a pain on the *** and it delete your infromation to uninstall ubuntu.  I hope it wasen't a mistake installing ubuntu on my system. Now I am working on my Windows XP. I have dual boot on my desktop since i cant live without the Adobe pack.

Contact me at: [email]Mohdweb@hotmail.com[/email] 

And if you are really sure about how to fix it please post it here so others can use it as a reference.

---

### Post by jim_p on 2007-09-08
It seems to me that you have installed the wrong drivers. Anyway, I will show you how to get back to the desktop and install the right ones.

1. Revert to Ubuntu's default nv driver. This can be done in several ways, choose the one you feel most comfortable with:
All these ways do the same thing but with different approach.

i) Boot your system using a live cd. (for the following I assume you are using Ubuntu 7.04 Live cd). Wait to get to the desktop, open up a terminal and type 
```
sudo gedit
```
That will open a text editor with root privileges. Look for a file named xorg.conf.
This will either be inside **/media/**(some name for your hdd)/etc/X11/
or **/mnt/**(some name for your hdd)/etc/X11/. Oce you have opened the file search for "nvidia" and substitute all of its instancies with "nv". Save, close and reboot.

ii)Get to a command line. This is done by selecting "Ubuntu... (recovery mode)" from grub. You will be asked for YOUR password and you will be given root privileges from this point. Type
```
vi /etc/X11/xorg.conf
```
A simple text editor opens up. Whatever you type from now on is written inside the xorg.conf file. Again search for "nvidia" and substitute with "nv". Once you are done press the **:** key to exit editing, then press **w** to save the file and **q** to exit that editor. Type "reboot" to reboot.

iii)Get to the command line as I described above. Type
```
dpkg-reconfigure xserver-xorg
```
A text based dialog appears (text on screen with yes/no selections below). Go though all the steps until you reach something that says about drivers and has a list below the text. Select "nv" from there, continue with the dialogs and  reboot once you are done with all that.

After you get yourself into Ubuntu (with graphical interface) use synaptic or apt-get to install **nvidia-glx-legacy** and you are done.
Why legacy(=old) ? Because your card is prior to the Geforce3 series.

---

### Post by Mohdgame on 2007-09-08
Thank's alot. I'll try that right away! Just being few minutes in windows without serious work makes me sick. I forgot to mention my card, its Geforce 6600. Stupid card but I'll replace it later. Hope this work :)

---

### Post by Mohdgame on 2007-09-08
It worked well, but still i can't get some effects and the refresh rate is stupid. 

What should i do now to enable some effects? I did it before in the same desktop before formatting my hard-drives.

[IMG]http://xs319.xs.to/xs319/07366/Screenshot-1.jpeg[/IMG]

Notice that I reinstalled my Nvidia-glx-legcy from package manager. ( I am not that good with terminal :P ) So, where is the problem? Why my Nvidia 6600 is not working well?

---

### Post by jim_p on 2007-09-08
Once again, I made a HUGE mistake!
I accidentally read Gforce2 on the 1st post, thats why i suggested nvidia-glx-legacy :( :(

Since your card is a 6600, it is much much newer than the Gforce3.
So you don't need the -legacy drivers.
You can blame me as much as you wish

I googled a bit for 6600 drivers and ubuntu and I saw that many people suggest to download the drivers from nvidia
So here they are [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html) along with the instructions

If you encouter any problem please come back here and tell me

---

### Post by Mohdgame on 2007-09-08
> **jim_p said:**
> Once again, I made a HUGE mistake!
I accidentally read Gforce2 on the 1st post, thats why i suggested nvidia-glx-legacy :( :(

Since your card is a 6600, it is much much newer than the Gforce3.
So you don't need the -legacy drivers.
You can blame me as much as you wish

I googled a bit for 6600 drivers and ubuntu and I saw that many people suggest to download the drivers from nvidia
So here they are [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html) along with the instructions

If you encouter any problem please come back here and tell me

No, No, its okay really. Thanks alot, really appreciated the help :D Gonna try the driver.

---

### Post by Mohdgame on 2007-09-08
Well, I got a problem. 

> Nvidia website instructions:Type "sh NVIDIA-Linux-x86-100.14.11-pkg1.run" to install the driver.
It didn't worked, I right clicked on and proprties and made it "Excutable" then i double clicked and i clicked on "Run in teminal" and i get a message right into my face "Nvidia driver must be run as root"e. I tried "sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run" and it didn't worked either. 

How can i run my system as a root?

---

### Post by Ranguvar on 2007-09-08
Ubuntu doesn't allow root login, you have to use sudo.

As in it still says it needs root? Does it ask you for your password?

---

### Post by merlinus on 2007-09-08
Perhaps this approach will help:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

-merlin

---

### Post by strabes on 2007-09-08
Paste the output you receive when you run: ```
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run
```

---

### Post by Mohdgame on 2007-09-08
> sh: Can't open NVIDIA-Linux-x86-100.14.11-pkg1.run

This is the output.


> Ubuntu doesn't allow root login, you have to use sudo.

As in it still says it needs root? Does it ask you for your password?

No, it doesen't. I can't do nothing, i can only press enter which kicks me out.
> 
Perhaps this approach will help:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

-merlin

Really appreciated. I will check it out.

---

### Post by jim_p on 2007-09-08
You run it as root but you will need to have set your root password first
```
sudo passwd root
``` and give the root account a password
After that navigate to the directory that the drivers are and do:
```
su
```
Now you are using the root account the "real" way, so
```
sh nvidia-whatever.run
```
and you are done

A few things I have to emphasize on...
This is the way that most linux distros enable the root account to do a system wide installation.
Ubuntu is NOT one of them sadly. In Ubuntu the user account is confused with the root account
and this leeds to these sorts of problems :(
The root command line ends in "#" while a user ends in "$" like so

jim@jim-desktop:~$ su
root@jim-desktop:/home/jim#

---

