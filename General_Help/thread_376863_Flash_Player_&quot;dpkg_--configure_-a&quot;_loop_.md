---
title: "Flash Player &quot;dpkg --configure -a&quot; loop please help"
date: 2007-03-05
forum: General Help
---

### Post by vishnu on 2007-03-05
A while ago I tried installing the non-free flashpluggin and it froze on me during install.  Now whenever I try and install anything else I get the following happen to me - It's like it's locked into completing the flash install and the "OK....." progress bat just goes on and on.  Is there any way to clear this job out of some cache?



matt@matt-ubuntu:~$ sudo apt-get install xmms
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
matt@matt-ubuntu:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--11:06:07--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.110.70
Connecting to fpdownload.macromedia.com|72.246.110.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .........

---

### Post by jimbob on 2007-03-05
Try removing it first -  sudo apt-get remove --purge flashplugin-nonfree

Then try to reinstall again.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

