---
title: "Cannot select beryl window manager"
date: 2006-11-20
forum: General Help
---

### Post by susu on 2006-11-20
Hello,

I have just install 6.06 (32 bit) and all the updates.  I cannot get beryl to work for some reason.  I have followed [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit) and got my nvidia driver set, glxgears runs perfectly, I've got the screen resolution right but I cannot get beryl to run...   I can click on Beryl Manager-> Select window manager-> Beryl then the screen flashes and then when I check it again, Compiz is selected, not Beryl. 

Can someone please help?

---

### Post by CowzRule on 2006-11-20
I installed Beryl using the guide at:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")
I never had Compiz installed, but from the info there I believe you'll need to remove Compiz first.
Hope that helps.

---

### Post by strabes on 2006-11-20
It's usually best to follow guides on the program's own wiki. In this case, the page that cowzrule is it. 3rd party guides never seem to work for anyone.

You have to remove Compiz before you upgrade to Beryl

---

### Post by susu on 2006-11-20
I've used "sudo apt-get remove compiz-gnome" to uninstall compiz..
Still no luck after rebooting.

Also. I'm using dapper not edgy so how will that guide help?

---

### Post by strabes on 2006-11-20
follow the dapper guide on that wiki. ([http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)) Then set beryl-xgl and gnome-settings-daemon to start up with gnome. (gnome-session-properties)

---

### Post by susu on 2006-11-20
Ok that looks a little different from what I've done.  I'll try it out as soon as I get home.  Thanks!

---

