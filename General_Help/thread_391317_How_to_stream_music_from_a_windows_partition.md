---
title: "How to stream music from a windows partition"
date: 2007-03-23
forum: General Help
---

### Post by gannina on 2007-03-23
Hi, i'm not very experienced at using Ubuntu. I was wondering if I could somehow access my windows partition in order to access my music and play it on Ubuntu, so I don't have to have the files on both OS's.

1. If that's possible, are my songs at risk for becoming corruptedt if I do this?
2. I use an audio player called foobar, is it possible to access foobar and play songs from my playlists that are on windows?

Thanks in advance

---

### Post by dfreer on 2007-03-23
Not only is this possible, but it should be fairly easy.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)
This link should help you in mounting your windows partition, and if you have a troubles after that you can always post back here. In fact, for those new to ubuntu that site (ubuntuguide.org) has some great how-to's. Use <Ctrl>+<f> and just look for whatever you want to accomplish ;)

1. Linux plays very nicely with fat32, and can read from NTFS without any problems. Of course, if you are really worried about corruption (you shouldn't be), you can always mount the windows partition as Read-Only so that linux can't write to it at all.
2. Hmmm. This is a bit trickier. Let me look that up, because there are several different solutions and I don't want to give you the wrong ones :)

---

### Post by dfreer on 2007-03-23
Ok. About foobar, or more specifically foobar2000.
What kind of playlist files does it use (.m3u for example)? Where does it store them on your windows partition?

It appears that some people have had limited success running the actual windows foobar2000.exe, so I wouldn't recommend that without trying it first.

[http://polishlinux.org/apps/mesk-audio-player-0-2-1/](http://polishlinux.org/apps/mesk-audio-player-0-2-1/)
This site appeared while googling, and it looks like it is a foobar2000 clone. Although you might want to try out Amarok, Songbird, XMMS, or Rythmnbox (all native linux music players). You may need to manually import your playlists, or even recreate them though.

---

### Post by gannina on 2007-03-23
Thanks for the help! I think the majority of my playlists are in .m3u (winamp format). I noticed in your post you made reference to Ubuntu Edgy, I think I'm running on Ubuntu Dapper, is it possible to upgrade to that without having to format anything?

---

### Post by gannina on 2007-03-23
I found a guide to upgrade Dapper to Edgy, i'll try the mounting thing :)

---

### Post by dfreer on 2007-03-23
Well, the command hasn't changed any so you can mount that partition with Dapper is you don't want to upgrade.
Upgrading is getting better and better, I upgraded from Edgy to Feisty with no problems. 
That ubuntuguide has a guide for both Edgy and Dapper, and soon it will have feisty too. Check the links near the top.

Also, .m3u is pretty commonly supported, most if not all of those music players I mentioned support it. I think you might need to edit a few paths though, I dunno. If you have problems getting the playlist working post your errors and the playlist file and someone should be able to help you :) Enjoy Ubuntu!

---

