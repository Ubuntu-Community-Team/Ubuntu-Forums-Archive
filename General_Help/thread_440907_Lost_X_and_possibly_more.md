---
title: "Lost X and possibly more"
date: 2007-05-12
forum: General Help
---

### Post by steevc on 2007-05-12
I started my system today and noticed that it did a scan of a partition due to errors, but then it dumped me at a shell. The system was shut down cleanly yesterday.

I saw a message about mdadm not finding any config, but I'm not sure if I need it anyway.

startx fails as it cannot find /lib/modules/2.6.20-15-386/volatile/nvidia.ko

I've also established that ldconfig is missing so apt-get is not working.

So in general it looks like something has got trashed. Any suggestions on what else I can check and any possible solutions?

I recently upgraded from Edgy to Feisty. That got an error during the upgrade, but I ran the suggested commands and it seemed to sort itself. I've been running Feisty for a couple of weeks. I do get odd problems with locking up or not shutting down properly, but these are fairly rare.

I have a Feisty CD so I could re-install if I have to. Luckily I have another PC in the room so that I can still access this forum.

If I were to re-install what's the best way to recover my existing user accounts? /home is on it's own partition.

---

### Post by Theimon on 2007-05-12
Something got trashed indeed so it seems. If you are going to do a fresh install, all you have to do is add the user(s) since you got /home on its own partition. Settings should remain just as they were. You have to install all the programs you are using now though.

---

### Post by steevc on 2007-05-13
I went for the reinstall and have recovered the user accounts. I'm just having a few issues with:

1. Video - I installed the nvidia legacy, but could not get my old 1280x1024 resolution until I had manually set up the monitor frequencies and run some other stuff. I still can't get over 60Hz at that, which is annoying. The wiki talks about using the Restricted Devices Manager to install nvidia drivers, but I don't see that in Kubuntu.

2. The keyboard settings were wrong, so I'm not getting the right UK characters (" and @). I've got it working on 2 accounts, but not on the other, even though they are all set up the same.

The install itself ran very smoothly and only took around 30 minutes. That's probably better than any Windows install I've done and is easier than previous Linux ones.

Update: and now apt-get is getting a segmentation fault :( Maybe a reboot will help. Fixed that by removing the files from /var/cache/apt

Oh, and I can't play mpegs in Kaffeine, vlc or mplayer - Sorted that by installing the extra codecs. Still get an error from K3B saying it can't decode MP3

---

