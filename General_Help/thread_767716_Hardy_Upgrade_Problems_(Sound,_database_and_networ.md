---
title: "Hardy Upgrade Problems (Sound, database and network)"
date: 2008-04-25
forum: General Help
---

### Post by neoncode on 2008-04-25
I've upgraded from 7.10 to 8.04 and I've run into a few problems... Firstly network is broken without reloading the forcedeth module with

```

sudo modprobe -r forcedeth
sudo modprobe forcedeth msi=0 msix=0

```

My networking is Ethernet on my nForce 680i Chipset motherboard. I had the same problem, with the same workarround, in the beta versions of Hardy I tried.

Secondly I use a MySQL database to store Amarok data and Amarok now seems to not get track info (playcount, rateing, lastplayed, ...) in the normal album view, but not when useing dynamic playists (one that gets all 5-star tracks still works for example, listing the tracks with all the data, but when I view the same track loaded from an album none of this info shows up)

Lastly, sound doesn't work. The only thing that outputs sound is KDE4's startup sound. 

Can anyone offer any help? If all else fails I have a ghost of my / partion (/home is separate) from before the upgrade to fall back too. But other than that it seems to have handled the upgrade well, bearing in mind my /home is a software RAID and my graphics driver is binary nVidia...

---

