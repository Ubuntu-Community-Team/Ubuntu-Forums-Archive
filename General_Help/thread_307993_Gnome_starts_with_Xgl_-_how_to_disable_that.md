---
title: "Gnome starts with Xgl - how to disable that?"
date: 2006-11-27
forum: General Help
---

### Post by rigol on 2006-11-27
Hi there,


Everytime I start Gnome, Xgl loads also. I have Beryl installed using this HowTo: [http://doc.gwos.org/index.php/BerylXglOnDapper](http://doc.gwos.org/index.php/BerylXglOnDapper)

Xgl loads even if I delete /usr/bin/beryl-manager from the startup-programs.

My problem is, I want to play GuildWars using Cedega, but that does not work with Xgl running. So I first followed this guide: [http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636) , but to no avail. The script works fine though, but when trying to install GuildWars with following terminal command:
```
nonXgl cedega /media/cdrom0/setup.exe
```
I get at the very end after downloading the client *"a serious error has occured"*

My question now is: how can I prevent gnome from starting with Beryl/Xgl?

---

### Post by CheeseEatingBulldog on 2006-11-27
You have to unload the XGL server,

In the file /etc/gdm/gdm.config-custom comment out the Servers and Server-Xgl. (like so)

# [servers]
# 0=Xgl

# [server-Xgl]
# name=Xgl server
# command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
# flexible=true

Then save file, and restart X (Ctrl + Alt + Backspace), this should start up X without XGL.

You might want to remove beryl from startup.

If you want XGL back you will have to un-comment the gdm file again.

---

### Post by rigol on 2006-11-27
Thanks,CheeseEatingBulldog! 

I read in an Edgy Beryl guide something about adding Beryl/Xgl to the Sessions at the login-screen, so I can choose it if I wanted. 
How would I do that in Dapper?


[edit]
I tried that but nothing changes. I still log in starting Beryl (I removed beryl-manager from the startup programs too, but it starts nontheless).
When trying "glxinfo | grep rendering" I get "direct rendering: no", when using "nonXgl glxinfo | grep rendering" I get "direct rendering: yes" - so the nonXgl script is working and I'm still in XGL.

---

### Post by strabes on 2006-11-27
you should have set up a separate gnome session like the 1st party howtos on wiki.beryl-project.org

don't follow 3rd party guides

---

### Post by rigol on 2006-11-27
strabes: Right, will follow your advise next time. But right now your post wasn't that helpful. 

Surely there has to be a way to get Gnome starting without XGL and wothout deinstalling Beryl?

---

### Post by CheeseEatingBulldog on 2006-11-28
I can only guess that maybe you have xgl in the actual gdm.conf, I am not that experienced with it, but I am assuming that the gdm.conf-custom file makes it possible to seperate xgl and gnome and maybe gdm.conf is the fixed file? 

Have a look in the gdm.conf file for servers xgl or something.

---

### Post by rigol on 2006-11-28
Alright... could someone please have mentioned that I need a complete restart? Not just X... :neutral: 

It's fine now, I'm booting again with normal Gnome, so your advice worked, thanks CheeseEatingBulldog!

---

### Post by CheeseEatingBulldog on 2006-11-29
Sorry, just rebooting X works for me, I have to disable XGL if I want to play CS via steam. And commenting out the XGL server and rebooting X always works.

Oh well, at least you're problem is gone.

---

