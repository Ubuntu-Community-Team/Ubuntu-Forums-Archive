---
title: "Easy question..."
date: 2006-12-19
forum: General Help
---

### Post by holdinout on 2006-12-19
OK, I've been looking everywhere trying to get my resolution higher than 800x600. Everything I try, is either an invalid command. I guess I don't have access to root? I was trying to edit xorg.config as I was told to do in order to change the resolutions, but I couldn't save it. 
I was also trying to install themes, but I couldn't save files into "\".
I found directions for installing my nVidia drivers, but one of the commands wouldn't work...Is this because of this, "It has come to our attention that some unofficial nvidia drivers may have been broken by the recent kernel update for 6.10 Edgy Eft."? It would have been nice to know that before I spent my night trying to install it ](*,) .Help would be appreciated, and if it's needed I can find all the steps I followed.

I was also trying to install themes, but I couldn't save files into "\".

Ooh, almost forgot:
OS - Xubuntu Edgy Eft
Monitor - Compaq MV920
Video Card - nVidia GeForce FX5200

---

### Post by aysiu on 2006-12-19
I think you should read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by holdinout on 2006-12-19
3 more things:

Xubuntu support dual monitor?
Whats the launch command for Terminal?
I saw vulnerabilities on the home page of the forum. Whats the command to download their updates?

---

### Post by holdinout on 2006-12-19
That was fast, lol. Thank you so much.

---

### Post by joneberger on 2006-12-19
hey holdinout.

concerning your desktop woes, i don't know how muchi can help.  i'm new to the ubuntu scene myself, but not so much linux.

for nvidia drivers the easiest thing for me has always been to go to the nvidia page and compile the sources.  download the file.  then from the logout screen do a alt+ctrl+f1.  this should take you a text-based login.  login as yourself and then do a sudo /sbin/telinit 3.  this changes the computer runlevel to 3 (no X).  then find that nvidia file and sh NV......  it should take you through a series of install steps.  when it asks if you want to let it alter your xorg.conf file, say yes.  if it has problems, note the error and come back here.   otherwise from your prompt  (as sudo still) type /sbin/telinit 5 and let it return to runlevel 5.  The logout and do a "alt+ctr+f7".  thiswill return you to your graphical login.   if the nvidia install works, it will actually probably fix your resolution errors.  i think the max res. is 1600x1200.  so see if that gets you anywhere.  

if your nvidia card has dual outs, you should seriously examine the TwinView property.  This is so much easier if you have two of the same monitor.  that's what worked for me in rh.  there is a thread in this forum for the official method of updating.  it should be at [http://ubuntuforums.org/showthread.php?t=286599]("http://ubuntuforums.org/showthread.php?t=286599").    xterm is a possible terminal.  if you can "run a command" or something that's the way to do it.  

good luck,

jon

---

### Post by aysiu on 2006-12-19
The easiest thing to do is compile the sources? Nope. It gets easier than that.

Just use the package manager to do that. Instructions here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by holdinout on 2006-12-19
Heres something I should probably ask... Is there some sort of in depth guide to the commands? Or just run the command as "xxxx --help"?

---

### Post by aysiu on 2006-12-19
> **holdinout said:**
> Heres something I should probably ask... Is there some sort of in depth guide to the commands? Or just run the command as "xxxx --help"?
These are all the commands you'll need for now:
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

I learned almost all the commands I know now from copying and pasting off that website.

---

### Post by holdinout on 2006-12-19
Problem solved for the most part... Icon text and Menu text within right-click is too small, almost too small to read... All the other text and everything else is fine though, thanks!

---

