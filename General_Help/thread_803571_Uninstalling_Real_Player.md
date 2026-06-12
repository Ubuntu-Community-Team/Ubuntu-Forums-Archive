---
title: "Uninstalling Real Player"
date: 2008-05-22
forum: General Help
---

### Post by thehereaway on 2008-05-22
hey, i installed Real Player about an hour ago because a friend sent me a file of something important that i couldn't convert. Its Real Player 11 GOLD and i installed using a .bin or something... 
[I]
(im not good with computers let alone linux, wouldnt be using it if i had the choice - no offense its just my windows, which was apparently an illegal copy, broke down and couldnt afford a new one) [/I]

...the problem is, i started up Amarok to play some music, and my speakers suddenly sound like utter crap! the quality has been distorted, so im trying to uninstall Real Player but have no idea how.

thanks.

P.S. Its not in the synaptic

---

### Post by drs305 on 2008-05-22
Amarok may have changed some settings in amarok. You might want to check Settings, Configure Amarok, Output Plugin and change Autodetect to ALSA (or another setting).

I'm looking for my notes on how I removed realplayer 11. I've installed and removed it multiple times.

---

### Post by thehereaway on 2008-05-22
> **drs305 said:**
> Amarok may have changed some settings in amarok. You might want to check Settings, Configure Amarok, Output Plugin and change Autodetect to ALSA (or another setting).

I'm looking for my notes on how I removed realplayer 11. I've installed and removed it multiple times.


thanks, 

this may seem stupid but i've gone to the configure Amarok settings but can't find where to change the Output Plugin?

EDIT: found it, it still sounds funny

---

### Post by drs305 on 2008-05-22
I found one of the methods I used to uninstall the RealPlayer11GOLD.bin

It is located at the bottom of the page, and there is a disclaimer about using the script. All I can say is that I used it and it seemed to work. Here is the link:
[https://player.helixcommunity.org/2005/help/playerfaq.html](https://player.helixcommunity.org/2005/help/playerfaq.html)

---

### Post by thehereaway on 2008-05-22
i've no idea how to use the Uninstaller :oops:

---

### Post by drs305 on 2008-05-22
Ok, I found it. When I created realplayer via bin, it created a folder on my desktop called hxsetup. In the postinst folder, run postuninst.sh and it will uninstall most of realplayer. If you installed it as root, use 'sudo postuninst.sh' . I then deleted the Realplayer folder. I think there were still some files in /opt/real or /opt/realplayer, which I just deleted with sudo.  Note: I couldn't click on the .sh file and get it to work. I had to run it in terminal, i.e. change to the postinst folder and run ' ./postuninst.sh '

If you install apps via non-standard means, it's best to keep any folders created because, as you can see, removal scripts are often kept in them and can't be found elsewhere. If you don't have the hxsetup any longer, just run the bin install again and then remove it. The folder is named hxsetup because it is part of helix's linux development.

---

### Post by thehereaway on 2008-05-22
> **drs305 said:**
> Ok, I found it. When I created realplayer via bin, it created a folder on my desktop called hxsetup. In the postinst folder, run postuninst.sh and it will uninstall most of realplayer. If you installed it as root, use 'sudo postuninst.sh' . I then deleted the Realplayer folder. I think there were still some files in /opt/real or /opt/realplayer, which I just deleted with sudo.  Note: I couldn't click on the .sh file and get it to work. I had to run it in terminal, i.e. change to the postinst folder and run ' ./postuninst.sh '

If you install apps via non-standard means, it's best to keep any folders created because, as you can see, removal scripts are often kept in them and can't be found elsewhere. If you don't have the hxsetup any longer, just run the bin install again and then remove it. The folder is named hxsetup because it is part of helix's linux development.

the hxsetup folder isnt on my desktop, i found it if i double click the original .bin file but i cant change directory to it, there is a postinst folder in a RealPlayer folder that has appeared next to the original bin file but i cant cd to that that either, only the RealPlayer folder. would the hxsetup folder be anywhere else on my computer? 

(i have no freaking idea how to find programme files using linux they make it so complicated unlike windows)

---

### Post by drs305 on 2008-05-22
Are you familiar with the forum's private messaging. I'll talk you through it  on that. Check the upper right of the page for the Private Messages link and click on it when it shows a message.

---

### Post by thehereaway on 2008-05-22
> **drs305 said:**
> Are you familiar with the forum's private messaging. I'll talk you through it  on that. Check the upper right of the page for the Private Messages link and click on it when it shows a message.

ok, cheers

---

### Post by gchatzim on 2010-04-12
THis is the automatic uninstall that what worked for me:

$ sudo -i
# /opt/real/RealPlayer/postinst/postuninst.sh
# rm -rf /opt/real/RealPlayer/

from
[http://ubuntuforums.org/showthread.php?t=920171](http://ubuntuforums.org/showthread.php?t=920171)

---

### Post by Soul-Sing on 2010-04-12
> **gchatzim said:**
> this is the automatic uninstall that what worked for me:

$ sudo -i
# /opt/real/realplayer/postinst/postuninst.sh
# rm -rf /opt/real/realplayer/

from
[http://ubuntuforums.org/showthread.php?t=920171](http://ubuntuforums.org/showthread.php?t=920171)

+1

---

