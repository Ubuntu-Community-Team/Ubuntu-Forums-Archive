---
title: "realplayer will not start"
date: 2005-07-08
forum: General Help
---

### Post by luvdemheels on 2005-07-08
I installed realplayer with synaptic and it shows up in the menu but when I click it it does nothing.  ](*,) The install said successful.

Will someone PLEASE help me troubleshoot and figure out why it is not starting??

---

### Post by mohaham on 2005-07-08
edit /etc/esound/esd.conf file
change 
auto_spawn=0 
to 
auto_spawn=1

here's my /etc/esound/esd.conf file:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100


then Restart Gnome

Hope this helps...

---

### Post by ecadre on 2005-07-08
Hi,

I'm not being funny, but here's a question.

Realplayer does not get installed by Synaptic, did you go through the procedure of downloading Realplayer and then installing it from the command line?

Also, Ubuntu (at the moment) will point you towards the version 8 of Realplayer.  What I did was to leave Synaptic and download and install Realplayer 10 for Linux.

It's here:

[http://www.real.com/linux/?rppr=rnwk&src=040104freeplayer](http://www.real.com/linux/?rppr=rnwk&src=040104freeplayer)

The installation is very simple.  They are on the Real website as follows:

#####################
Installation Instructions

 - Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window. 

 - Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

 - When you launch the player for the first time, a set-up assistant will take you through configuring your player. 

 - Enjoy your RealPlayer10 for Linux!
#####################

I installed Realplayer in a directory off my home directory.  If you put a dot "." at the beginning of the directory name then it will be hidden and will not clutter up your normal view of the home directory.

if you want to persevere and solve the problem with your Realplayer 8, then we need a bit more information.

Like:  * where did you install it?
         * what command did you use to install it?
         * what permissions does the directory (and the files) where it's installed     
           have?

In the end I'd rather not have to use Realplayer, but it's needed to listen to or watch stuff on the BBC website  :(

---

### Post by Shinitenshi on 2005-07-09
Yes you first have to install realplayer and then install it from the synaptic. the install u find in synaptic put the shortcutz stuff like that but your main installation is where ever u installed it based on the information from realplayer site.

I had the same problem as u a couple days ago and i got it solved here's the thread:
[http://ubuntuforums.org/showthread.php?t=47162](http://ubuntuforums.org/showthread.php?t=47162)

---

### Post by NeoChaosX on 2005-07-09
[This post will get RealPlayer working properly. It did for me.](http://ubuntuforums.org/showpost.php?p=80282&postcount=21)

---

