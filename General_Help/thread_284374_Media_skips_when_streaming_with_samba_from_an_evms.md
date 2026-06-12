---
title: "Media skips when streaming with samba from an evms partition"
date: 2006-10-25
forum: General Help
---

### Post by mani99 on 2006-10-25
I have a Kubuntu server with 4 320gb Seagate 7200.10 harddrives
with a single 881gb ext3 partition created using evms (raid5).

When opening media files stored on the partition on any other 
computer the video skips at least once every 5 minutes. The skip can be up to 10seconds at a time and it's VERY irritating. 

I have opened many different video files, from short low-bitrate clips to full 1080p movies, and even tried a direct gigabit connection between two computers and there is no difference. Even music suffers from this skip.

I have used vlc and mplayer on both Kubuntu and Windows with the
same results.

If you want to see some .conf files or screenshots just ask.

---

### Post by Jussi Kukkonen on 2006-10-25
As far as my experience goes, samba is the problem. I couldn't get my (pretty similar, although not raid) setup to work however I tweaked it, until I tried NFS: not a single problem after that.

---

### Post by mani99 on 2006-11-06
Thanks for the reply, It really works better. I also have some windows computers that need to be able to access the share, is there a simple way to make that work?

---

