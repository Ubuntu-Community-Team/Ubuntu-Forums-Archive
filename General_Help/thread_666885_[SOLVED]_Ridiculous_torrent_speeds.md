---
title: "[SOLVED] Ridiculous torrent speeds"
date: 2008-01-13
forum: General Help
---

### Post by ~LoKe on 2008-01-13
Well...I've started a download of an Ubuntu CD Image that has about 130k seeds and 30k leechers, but I'm only getting 170kbp/s (I've seen it hit about 270 a few minutes ago).  The odd thing is, I have a 6mb down connection.

Now, what interests me is that my upload is only at 0.3kbp/s, and I've got it set to unlimited, so it should be skyrocketing.

I'm using rTorrent, and here's my config (only the uncommented lines):
> download_rate = 0
upload_rate = 0

directory = ~/Downloaded/

schedule = watch_directory,5,5,load_start=~/Torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=~/Torrents/*.torrent

port_range = 6900-6910

port_random = no

use_udp_trackers = yes

I've tried KTorrent and uTorrent and don't remember the speeds, but I'll give Deluge a shot in a minute.  Also, the ports are forwarded on my router.  I've uninstalled IPTables.  What could be interfering?

**EDIT**: Same speed in Deluge.
**EDIT2**; 750+ kbp/s using port 50000.  Which I never opened...odd.

---

### Post by brennydoogles on 2008-01-13
I'll tell you that I too have had a hard time with decent torrent speeds. I will watch the thread a bit, and hopefully we can come up with something workable.

---

### Post by rune0077 on 2008-01-13
If you've only just started the download be patient. Speed should pick up as you get more packages available and start distributing them to others - the higher your upload and the more packages others are receiving from you, the higher your download speed.

---

### Post by ~LoKe on 2008-01-13
> **rune0077 said:**
> If you've only just started the download be patient. Speed should pick up as you get more packages available and start distributing them to others - the higher your upload and the more packages others are receiving from you, the higher your download speed.

Changing to an incredibly high port solved my problem.  Looks like my ISP is throttling.

---

### Post by SOULRiDER on 2008-01-13
> **~LoKe said:**
> Changing to an incredibly high port solved my problem.  Looks like my ISP is throttling.

Yes, its possible and its horrible. 150 kb isn't bad at all though, at that speed it takes like what, hour and a half to download the image?

Anyways, please mark the thread as solved.

---

### Post by rune0077 on 2008-01-13
> **~LoKe said:**
> Changing to an incredibly high port solved my problem.  Looks like my ISP is throttling.

Your ISP should only be throttling default BitTorrent ports (actually they shouldn't, but they do). Still, many torrent how-to's states that high ports are safer (don't know why that is, though). I just use Deluge and has it set for random ports, and it always picks ports in the range of 20.000 - 60.000

---

### Post by Schalken on 2008-01-13
Also make sure your not comparing bits with bytes. a 6Mbps (megaBITS per second) connection is a 0.75 MBps (megaBYTES per second) connection. 1B (byte) = 8b (bits) Bits are used to measure connection speeds, bytes are used to measure transfer speeds, so make sure you convert between the two before comparing.

---

