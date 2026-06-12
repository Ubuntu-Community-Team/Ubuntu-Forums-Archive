---
title: "Flash download &amp; install"
date: 2007-05-29
forum: General Help
---

### Post by AllanP on 2007-05-29
Has anyone other than myself had problems downloading or installing flash. Automatix2 fails on install; probably timed out on download. I've been downloading for over four hours now and have 22% of "install_flash_player_9_linux.tar.gz"; a 2.5MB file.

---

### Post by greybirds on 2007-05-29
Feisty can install Flash for you itself, and automatically. You can either go to Applications > Add/Remove and search for "Flash" or open Firefox, go to a page that requires Flash, and confirm that you want to look for plugins.

Hope this saves you a long wait on that download.

---

### Post by AllanP on 2007-05-30
Didn't work; got to about an 8th of an inch from the end of the progress bar after almost five hours and quit. Oh well I finally got the downloaded file which I'll hang on to for future installs.

---

### Post by aysiu on 2007-05-30
It sounds to me as if something is wrong with your internet connection.

If not, there are about four other ways you can try to install Flash:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Crafty Kisses on 2007-05-30
> **aysiu said:**
> It sounds to me as if something is wrong with your internet connection.

If not, there are about four other ways you can try to install Flash:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Yeah it does sound like something is wrong with your connection, do you possibly have any Firewalls or anything to that nature going?

---

### Post by AllanP on 2007-05-30
Just the norm. Everything else works great. That is the only site I've had a problem with. I download distros frequently with no prob. I've gone to [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) with very good results; can't remember them off hand but, it is definitely not my connection. This Adobe page has been a problem to me on several occasions when trying to download flash. Well I finally have it and will save it for other distros.

---

### Post by Shadoweater12081980 on 2007-05-30
Do you have the latest browser? This may be the issue with the autoinstall. I remember the old days of plugin installs

ln -s /bin/lib/flash/i386 or whatever. GAH!!

---

### Post by AllanP on 2007-05-30
Yup 2.0.0.3 on auto update. Are you saying you can download it without a problem? It should take well under a minute not five hours.
I should try it with Opera. Never thought of that.

---

### Post by Crafty Kisses on 2007-05-30
> **AllanP said:**
> Has anyone other than myself had problems downloading or installing flash. Automatix2 fails on install; probably timed out on download. I've been downloading for over four hours now and have 22% of "install_flash_player_9_linux.tar.gz"; a 2.5MB file.

You should try installing SwiftFox, it's an optimized version of FireFox.

---

### Post by AllanP on 2007-05-30
I did and destroyed my java so went back to Firefox (which I like anyways).

---

### Post by jamesden_ip on 2007-08-23
I am having the same issue, I have even tried it at different location just in case of a firewall issue. can some one please help. here is what I am getting in the terminal window after the automaix failure...

Please help

[INDENT]james@james-laptop:~$ sudo apt-get remove flashplugin-nonfree 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
james@james-laptop:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.48.0.0ubuntu1~7.04.1) ...
Downloading...
--06:57:38--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.114.70
Connecting to fpdownload.macromedia.com|72.246.114.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

    0K .....
[/INDENT]

---

### Post by AllanP on 2007-08-23
I've no idea why it takes so long in LInux. I've had the same problem in Fedora. Windows takes seconds to install the plugin.
I downloaded the file from Adobe. It took a long time and I saved the file and installed it in ubuntu and Fedora.
Another time I just clicked on "Install plugin" after Firefox's "missing plugin" notice. Here again it took a long time but, did in the end complete the install.

Regards, Allan

---

### Post by Bablefish on 2007-08-23
Why does everyone seem to miss this...there is 2 very easy way to install flash in Linux. First go to a flash heavy site like [www.angryalien.com](www.angryalien.com) and click on the Firefox link to download the Flash plugin or simply go to Add Remove on your own system IT'S THERE!!!!!

---

### Post by jamesden_ip on 2007-08-23
Issue solved. It seems to be a firewall issue after all. I took the machine and put is directly to my my addtran just before the firewall, set the ip and everything works like a champ. Took less than a minute to install the flash plugin... 

I just can not figure out what is set up wrong in the firewall.

thanks for you help

Bablefish, I didn't miss it, it just didn't work.  when you went to dl the plug in the connection timed out, even if I tried [www.adobe.com](www.adobe.com) the site never loads. but I can visit every other site I tried with out fail. puzzling.

JD

---

