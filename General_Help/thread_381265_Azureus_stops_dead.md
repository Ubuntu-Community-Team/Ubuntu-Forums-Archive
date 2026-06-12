---
title: "Azureus stops dead ??"
date: 2007-03-10
forum: General Help
---

### Post by hppyfngy on 2007-03-10
Hey Why would Azureus stop downloading after just a few minutes?

I started a download on my new Edgy setup and the same torrent on my XP machine and after an hour the one on Edgy has 3.3mb down and has stopped and the one on XP has finished @ 699 mb.  

I have my ports forwarded correctly and it seems like all my settings are the same...

Also, if I stop and restart the torrent, it seems to take off for a few minutes then trickles back down to 0 down and 0 up.

Any ideas?    :confused: 

Azureus v2.5.0  on Edgy, 2.5.0.4 on XP

---

### Post by hamiltonlight on 2007-03-19
Hi

I'm finding I have the same issue. Did you ever find out what the problem was?

---

### Post by hppyfngy on 2007-03-20
> **hamiltonlight said:**
> Hi

I'm finding I have the same issue. Did you ever find out what the problem was?

Nope

I uninstalled and reinstalled, triple checked ports and tested NAT and still the same issue.

---

### Post by snake98 on 2007-03-20
I had this same problme what i did to fix it was install sun java, and download azureus from sorgeforce and install in manually, here some commands and webpages to help you out.

Download Azurus from (instructions from [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29))

```
wget http://kent.dl.sourceforge.net/sourceforge/azureus/Azureus_2.5.0.4_linux.tar.bz2
sudo tar jxvf Azureus_2.5.0.4_linux.tar.bz2 -C /opt/
sudo gedit /usr/share/applications/azureus.desktop
```

    * Add the following to the new file 
```

[Desktop Entry] 
Name=Azureus
Comment=Java BitTorrent Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;
```


now download sun java
```

sudo aptitude install sun-java6-jre sun-java6-plugin

```
now reconfigure to use sun java with this command

```
sudo update-alternatives --config java

```
then choose sun java, the download from the repository doesn't work with sun java for some reason, probably becuase it was compiled with an alternative

---

### Post by snake98 on 2007-03-21
Well that will postpond the problem, I have to restart my router, which is an old linkys BEFSR41 V2, and it now is working fine, but i will be changing it out.

---

### Post by hamiltonlight on 2007-03-21
I actually installed Azureus using the guide initially but did not change the jre to Sun's. After doing that I am currently seeing decent and sustained rates of transfer. Will leave it running overnight to see if it stalls out. Looking good so far however. 

Thanks for the pointer.

---

### Post by snake98 on 2007-03-21
This looked like it solved my problem, My router needed to be reset, and Moving over to Sun Java solved my problem, been downloading for almost a day without any real problems.

---

### Post by bmagyarkuti on 2007-03-22
Thanks guys, I have been looking for a solution on this problem for so long. I should have thought the problem was with gcj, as I had some issues with it at Fedora before. Anyway, you saved my life, so thanks again.

Additionally I am glad to announce that your solution works on the latest preview release of 7.04 Feisty, as well.

Greetings.

---

### Post by Kramxel on 2007-03-25
I'm so happy to have finally found the answer!
Azureus didn't connect to most peers, and when it did it came up with the following message:
"Waiting for handshake"
And wouldn't connect...

I'm glad to snake98, who gave me the "secret" handshake :)

---

### Post by MikeDX on 2007-03-25
Thanks for the tip. installing java vm 6 fixed my problem!

---

### Post by mungy on 2007-04-25
I was having this same problem. Installing Java6 seems to have fixed the problem for me. Many thanks. :KS

---

