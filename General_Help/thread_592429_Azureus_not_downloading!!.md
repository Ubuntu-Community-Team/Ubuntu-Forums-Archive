---
title: "Azureus not downloading!!"
date: 2007-10-26
forum: General Help
---

### Post by jocku on 2007-10-26
I do believe I was able to download torrents with Azureus when I had 7.04. Now that I've upgraded to Gutsy Gibbon I no longer can. My girlfriends laptop has Windows XP and I have installed Azureus in it and it downloads good. So, the problem is probably not in the router or switch, because both computers are in the same wireless LAN. I've tried opening the proper port in Firestarter and shut it down. Nothing helps. It just says 0 peers and 0 seeds, which is not true.

Thanx in advance.

---

### Post by jocku on 2007-10-27
...or, actually it can see the Peers 0(62) and Seeds 0(27). I'm just not connected to any of them. Tried re-installing Azurus in Synaptic Package Manager, but it did not help. The UPnP function is enabled in Azures, my switch and also in my router. So the information ought to have a path to find it self from the Internet to my computer. Anyone have any ideas what I should try to do next?

---

### Post by por100pre1 on 2007-10-27
Install Deluge:

```
sudo aptitude install deluge-torrent
```

Have you tried opening the ports using Firestarter?

---

### Post by jocku on 2007-10-27
> **por100pre1 said:**
> Install Deluge:

```
sudo aptitude install deluge-torrent
```

Have you tried opening the ports using Firestarter?

Yes, I have opened the ports using Firestarter. It doesn't help.
I also installed Deluge.. Seems like a nice fast program. But same problem there.

---

### Post by por100pre1 on 2007-10-27
You enabled UPnP in your router. Did you open the ports in your router? If that's is not enough, try moving your PC to your router's DMZ.

---

### Post by stomponthis on 2007-10-27
I rekon deluge is way better than Azureus~!!
But anyway...
Check your ports are properly selected and forwarded, and not selected to random port numbers.  
I had a similar problem the other day, in my case I did not have permission to write onto the new partition I had made and had no idea why it wasnt downloading! lol

---

### Post by por100pre1 on 2007-10-27
Good one StompOnThis! Jocku, sometimes I just removed the ~/.azureus folder. Sometimes it fixes Azureus issues.

---

### Post by jocku on 2007-10-27
I tried removing the ~/.azureus folder. It didn't help. I also added my computers ip to the DMZ in my switch(2). Still nothing. In my router(1) there is no such function. There I can only put the port in the NAT system, which also does not help.

To clear up things a bit... I have:
(1)Prestige 660R-61, which is the adsl modem(router). Its ip is 192.168.1.1 (has UPnP)
this is connected to a:
(2)D-Link DI-524. 802.11g/2.4GHz Wireless Router(switch). Its ip is 192.168.0.1 (has UPnP)

My computers ip is 192.168.0.136. It is, like the other Windows XP computer, connected via wlan to the D-Link(2). Azureus is using the port 6881. Should I in the NAT system in my router(1) put the port 6881 to be forwarded to 192.168.0.1 or 192.168.0.136? This, in this point, does actually not make any difference, because Azureus (or Deluge) is not downloading anything in either way! How about the UPnP in Azureus and in my router(1)/switch(2)... Should i disable it?

Thank you for your help... What do you think I should try to do next?

---

### Post by mcneany on 2007-10-29
Same issue - exactly - Please post your solution when you find it. Thanks !

---

### Post by Iloru on 2007-10-30
I have also encountered this problem.  I've changed settings, tried uninstalling/reinstalling and it just won't work.  I did not have troubles before the 7.10 update so I'm under the impression it doesn't have anything to do with router settings, since those haven't changed in the least.  Hopefully someone can get to the bottom of this.  I don't *need* Azureus, but it's nice to have around on occasion.  :)

EDIT:  Okay, so I spoke too soon.  While I still haven't gotten Azureus to work, I've installed Deluge and found that it works just fine.

---

### Post by jocku on 2007-10-30
> **Iloru said:**
> I have also encountered this problem.  I've changed settings, tried uninstalling/reinstalling and it just won't work.  I did not have troubles before the 7.10 update so I'm under the impression it doesn't have anything to do with router settings, since those haven't changed in the least.  Hopefully someone can get to the bottom of this.  I don't *need* Azureus, but it's nice to have around on occasion.  :)

EDIT:  Okay, so I spoke too soon.  While I still haven't gotten Azureus to work, I've installed Deluge and found that it works just fine.

I too have made some sort of progress. First of all, I have given up with Azureus. It pisses me off. So I am now only using Deluge. I don't now what I did, but I was able to download one torrent with full speed, but now I'm back to where I started. It is not downloading anything. I still am not sure how I should do the port forwarding (which I was asking about earlier) or how I should do with the UPnP?

---

### Post by jocku on 2007-10-30
Ok, problem fixed !!!!!! I now use Deluge and It is working perfectly. If I would not have removed Azureus it would probably also work. The thing was that I was using the wrong port (6881). It is probably being blocked by my ISP. Now I use the port From: 64444 To: 64444 (=only 64444). 
I went to Deluges homepage [http://deluge-torrent.org](http://deluge-torrent.org) and downloaded the newest version (0.5.6.1). I only had to click on 'Download' -> 'Ubuntu' -> version (for me 'Ubuntu 7.10 (Gutsy Gibbon) package for i386 systems') and chose to open the file with Package Installer. After this I only had to click on the 'Install Package' button. Deluge can be started from 'Applications' -> 'Internet' -> 'Deluge BitTorrent Client'.

I have now also disabled DMZ in my wlan router and disabled port forwarding in my modem. The UPnP is also disabled in my router, modem and Deluge. Pretty stupid of me not figuring this thing out. It is even said in the Deluge installation process that you are not recommended to use the ports 6881-6889.

Damn, feels good to download again :)

---

