---
title: "Unable to load Webmin at startup"
date: 2005-07-04
forum: General Help
---

### Post by Screwball on 2005-07-04
I have just attempted to install Webmin-1.210 following the instructions in [this post](http://www.ubuntuforums.org/showpost.php?p=30701) . Everything **except** the "start at boot time" appeared to work correctly. Sadly, I received the following error:-
```
Failed to open /etc/rc.d/init.d/webmin :  No such file or directory
```This is understandable, as the startup scripts are in /etc/rc<runlevel>.d/S<2 digit sequence>whatever (these are symlinks to "../init.d/whatever").  Note that I was **not** presented with the "operating system" or "version" prompts - all other prompts appeared and were allowed to retain their default settings.

Could anyone advise me on how to get webmin started at boot time please. ](*,)

---

### Post by defkewl on 2005-07-04
I usually download from webmin.com and install it, instead of using the deb packages.

---

### Post by Screwball on 2005-07-05
I followed the instructions in the post I linked to - downloaded webmin-1.210.tar.gz from [http://www.webmin.com/download.html](http://www.webmin.com/download.html) - not a package (deb(ian?)) or otherwise afaik.

---

### Post by defkewl on 2005-07-05
[QUOTE=Screwball]I followed the instructions in the post I linked to - downloaded webmin-1.210.tar.gz from [http://www.webmin.com/download.html](http://www.webmin.com/download.html) - not a package (deb(ian?)) or otherwise afaik.[/QUOTE]

You can install webmin with apt-get but it never worked for me. That's why I downloaded the ones from webmin.com

---

### Post by Screwball on 2005-07-06
[QUOTE=defkewl]You can install webmin with apt-get but it never worked for me. That's why I downloaded the ones from webmin.com[/QUOTE]
Thanks for trying to help - but I thought I'd made it perfectly clear that I **had** downloaded directly from webmin.com...
No packages
No apt-get

---

### Post by crxyem on 2005-08-09
[QUOTE=Screwball]I have just attempted to install Webmin-1.210 following the instructions in [this post](http://www.ubuntuforums.org/showpost.php?p=30701) . Everything **except** the "start at boot time" appeared to work correctly. Sadly, I received the following error:-
```
Failed to open /etc/rc.d/init.d/webmin :  No such file or directory
```This is understandable, as the startup scripts are in /etc/rc<runlevel>.d/S<2 digit sequence>whatever (these are symlinks to "../init.d/whatever").  Note that I was **not** presented with the "operating system" or "version" prompts - all other prompts appeared and were allowed to retain their default settings.

Could anyone advise me on how to get webmin started at boot time please. ](*,)[/QUOTE]


I have the same exact issue. followed all the install directions to a "T" 
I just haven't figured out how to get this to run at system boot. 

anyone have a solution for this yet ??

---

### Post by Screwball on 2005-08-10
Maybe...

What I did eventually was to install the older version (see link in my earlier post) and then upgrade it - but **not** by downloading and installing a full version. That simply doesn't work due to the incorrect version detection.

---

### Post by Maxplayer14 on 2005-08-10
[QUOTE=Screwball]Maybe...

What I did eventually was to install the older version (see link in my earlier post) and then upgrade it - but **not** by downloading and installing a full version. That simply doesn't work due to the incorrect version detection.[/QUOTE]
 I have never got it to work.  And the problem actually isn't it starting at boot.  It is is working period after a reboot.  I can get it to work on the initial install, but after you reboot it won't work.  I have tried downloading from apt-get, downloading from webmin.com, everything, I can't it to work right no matter what.

---

