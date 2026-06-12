---
title: "Transmission Restart Issues"
date: 2017-01-02
forum: General Help
---

### Post by raccoonstrait on 2017-01-02
I have been using Transmission for several years now. Recently I noticed some changes in how it works. In the /home/user/.config/transmission/torrents folder, .added has been added after the .torrent extension. Consequently, when I restart Transmission it does not appear to recognize my ongoing torrents. There is also a /resume folder with the .resume extension replacing the .torrent  and/or .torrent.added extensions. 

If I use the Open button on the torrents folder, I have to change the selection from torrents to all files to be able to see the torrents. When I ask it to start these torrents I sometimes get information in the main window saying that it is downloading metadata, which never completes. Other times, it goes through a process of verifying local data and restarts the downloads/seeding. Using the Open button on the /resume folder seems to have no impact, it does nothing. I have lost a couple of downloads, both partial and full (at least as far as Transmission is concerned) and have to then go find the magnet links again and try to add them. Sometimes this leads to Transmission reporting a duplicate thread, even though none appears. Sometimes it works correctly. In the past, when I opened Transmission, it automatically restarted both downloads and seeding on its own.

This is the first time I have had such issues with Transmission. It has been performing very well for a long time. I have also used it on Debian via Raspberry Pi's without issue. I did try to remove Transmission and re-install (using aptitude purge and aptitude install) but it did not appear to impact the behavior. The current Transmission version is 2.84 (14307). The online help file is old and requesting updates (I guess from users). The same version of Transmission is on the Debian Pi's, and it auto starts without any assistance, and there is no .added appended to the .torrent files in /transmission/torrents.

I am running Ubuntu 16.04.

Any thoughts or suggestions?

Thanks

RaccoonStrait

---

