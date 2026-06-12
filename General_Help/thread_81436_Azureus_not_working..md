---
title: "Azureus not working."
date: 2005-10-24
forum: General Help
---

### Post by PriceChild on 2005-10-24
I'm using Eciadsl to access the internet with a usb adsl modem.

Everything else seems fine, however Azureus will not start downloading anything! It can check for updates, figure out which are needed and display them in the torrents, but they won't actually download either.

I have tried upgrading to the latest version but nothing's changed :(

I have tried using it's own "NAT/Firewall checker" and it says that it's fine on port 6881, but still won't download.

I'm running a dual boot pc and windows allows it to work fine.

Please help,
              Pricey

---

### Post by Kyral on 2005-10-24
Mind pasting the output from

```
sudo iptables -L -v
```

Maybe an iptables rule got added.

---

### Post by PriceChild on 2005-10-24
```
Chain INPUT (policy ACCEPT 269 packets, 95011 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 257 packets, 21288 bytes)
 pkts bytes target     prot opt in     out     source               destination 
```

---

### Post by Kyral on 2005-10-24
No firewall...

Either your ISP started blocking BT (Do other clients like BitTornado and QtTorrent work?) or Azureus has a bug.

---

### Post by evil-boweevil on 2005-10-24
Same thing here.  It looks like all the bittorrent clients I have tried in Ubuntu do not work.  I've tried bittornado Azureus and the gnome bittorrent client thing.  My mac running on the same network runs all bittorrent clients perfectly.  I would think it would be a Ubuntu problem.

---

### Post by PriceChild on 2005-10-24
Seems like it's Azureus :( Hey ho... will uninstall and download the source to install again.

Thanks for help anyway.

gnome bittorrent works fine.

---

### Post by Kyral on 2005-10-24
Remember to file a bug with SOMEONE so that it can be fixed ;P

---

### Post by F for Fragging on 2005-10-24
Same here. Didn't test if GNOME-Bittorrent works, because GNOME-Bittorrent uses an old version of Bittorrent shipped with Ubuntu, which is now banned by most trackers. So I immediatly tried Azureus.

I experienced the same. No NAT problem, health of the torrent is fine (green smilie), there are seeds/leechers, but it doesn't download or upload anything. On Windows I used Azureus, and currently use BitComet, and they both work fine.

So I tried download the latest Bittorrent beta 4.1.6 from bittorrent.com. Bittorrent does download my torrents properly. But I'd still like to use Azureus because it has UPnP. Azureus far from perfect though, it uses Java, the amount of features it posesses is overkill and it eats systems resources for dinner. I really miss a good Bittorrent client for GNOME.

---

### Post by evil-boweevil on 2005-10-24
Yup thanks.  Installed the official bittorrent client and it works.

---

### Post by RAOF on 2005-10-24
Have you installed the Sun Java runtime?  For me, at least, Azureus plays extremely badly with the gnu runtime included in breezy by default.  Oh, and if you have installed the Sun runtime, did you remember to update-alternatives --config java?

If none of this seems familiar, try [this howto]("http://www.ubuntuforums.org/showthread.php?t=70428&highlight=java+package") for the java runtime, then run
```
sudo update-alternatives --config java
```
and select the new Sun runtime.

---

### Post by F for Fragging on 2005-10-25
Thank you very much RAOF! Azureus works fine now, the download speeds are great :D. I had already installed Sun's Java, I followed the instructions on this - [https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca) - wiki page. Now that I read it again, I see it also mentions that selecting the default java version is necessary on Breezy, somehow I missed that when I was reading the installation instructions.

---

### Post by nedkelly on 2005-10-25
Yes thanx RAOF, had the same problem

---

### Post by Samuel on 2005-10-26
thanks RAOF this has been doing my head in for 2 days, needed to update the alternatives too, once again this forum proves to be the best linux support i have ever had :)

---

### Post by Treq on 2005-10-27
Thanks RAOF, sometimes it looks so complicated -and turns out to be so simple..
:) 
:Treq

---

### Post by mikwig on 2005-11-08
[QUOTE=RAOF]Have you installed the Sun Java runtime?  For me, at least, Azureus plays extremely badly with the gnu runtime included in breezy by default.  Oh, and if you have installed the Sun runtime, did you remember to update-alternatives --config java?

If none of this seems familiar, try [this howto]("http://www.ubuntuforums.org/showthread.php?t=70428&highlight=java+package") for the java runtime, then run
```
sudo update-alternatives --config java
```
and select the new Sun runtime.[/QUOTE]


Thankyou - this was all I needed too

---

