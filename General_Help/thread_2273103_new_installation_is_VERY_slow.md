---
title: "new installation is VERY slow"
date: 2015-04-10
forum: General Help
---

### Post by Jmolli on 2015-04-10
Hello, 

I just installed Xubuntu on old workstation of mine. Aim was to set it up as a fileServer/plexServer, but now I am beginning to doubt it since the performance is not what I expected.

**Computer Specs:**
HP XW6400 workstation 2xQuadcore xeon E5335(8 cores), 4 gigs of ecc ram, I know that its quite outdated but still should run xubuntu smooth ? (It did run windows7 very well)

Xubuntu 14.10 (utopic unicorn) installed on 250gb HD (ext4)/ of that 10 gigs is reserved for swap (no raid, 7200rpm generic sata drive)

I have another 1000 gb drive (xfs) that serves atm as a media library for plex

plan was to buy more drives and add another raid 5 setup to the machine which would then serve as a samba fileserver.

So like I said it is really fresh install. I did install samba, xrdp, plex, nvidia drivers, turned ufw on and updated everything.... and thats pretty much it.

It feels sluggish, So far its been running "rocksolid", but it is just very slow! Sometimes just opening a thunar window takes up to 10 second. Does anyone have any ideas where to start trouble shooting the problem... I still would like to make fileserver out of this machine, and I think it is very capable of serving as one. 

-Juha

---

### Post by The Cog on 2015-04-10
That is very abnormal - the machine should fly. I have used xubuntu on netbooks and they're nothing like that.

You could try running top (command line program) to see if the CPU is being hammered but I doubt that's it Top also shows the percentage of CPU time in **wa** state (waiting for disk) which should not be above a few percent. My first suspect would be the hard disk - are the drivers struggling, or seeing lots of errors? Ctrl-Alt-F1 and look for console error messages (Ctrl-Alt-F7 to get back to the GUI) or run the command **dmesg** and look for error messages. My second suspect might be the video card - maybe it's having trouble rendering the GUI on a strange video adapter.

---

### Post by Jmolli on 2015-04-11
Hey, Thnx for the tips.

However I didn't see anything out of ordinary doing the test you pointed out. I think that the slowdowns have had something to do with the fact that I have been logged in locally and from xrdp simultaneously. after fresh restart it does feel better.

I think I am going to forget my problem since in the purpose intended for the machine it is performing "well enough". When I get the new drives for storage I will get small/cheap ssd drive for the operating system and do a reinstall. I don't really know if its really affecting the performance all that much on fileserver use, but doesn't affect to the budget much either.

so thx again, and sorry for wasting your time.

---

