---
title: "[SOLVED] Does DVD-RAM work well?"
date: 2008-04-02
forum: General Help
---

### Post by YAOMTC on 2008-04-02
I'm thinking of buying a few DVD-RAM discs, but I first need to know how well Ubuntu handles them. Do they work well?

I ask this because I once bought a couple DVD-RWs, and couldn't manage to format them. I'm hoping that if I get those DVD-RAMs, I can just treat it like a flash drive and not have to go through that sort of thing.

Yes, [my drive](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106057) is compatible with DVD-RAM apparently.

---

### Post by YAOMTC on 2008-04-02
.

---

### Post by YAOMTC on 2008-04-03
.

---

### Post by YAOMTC on 2008-04-03
.

---

### Post by YAOMTC on 2008-04-04
.

---

### Post by YAOMTC on 2008-04-04
.

---

### Post by StOoZ on 2008-04-04
Well never tried DVD-RAM's even tough my burner supports them
but I use DVD-+RW's alot , without any problems. 
using nero for linux

---

### Post by milehigh on 2008-04-04
I installed a Plextor PX-800A last week, and so far it's working OK. To back up files on a DVD-RAM, you just drag & drop using Nautilus. I primarily bought it so I could read DVD-RAMs that I record on my Panasonic DVR, which has a hard drive and a DVD burner, but only supports DVD-R and DVD-RAM (not RW).

In case you want to read video files on a DVD-RAM from a DVR or camcorder, here's what I experienced:

When I tried to play the disc in gxine, I got errors that "the xine engine could not start" and that it was "missing a plugin". When I tried to open the directory containing the .VRO file, I didn't have permission, even as root. So I tried this:

sudo chown -R *user* /media/cdrom0/

Then I was able to open the directory in Nautilus and access the .VRO file. I copied the file to my hard drive; it plays OK in Movie Player, but in gxine the sound is out of sync.

---

### Post by YAOMTC on 2008-04-06
Alright, thanks! I'm gonna buy some then.

(I don't have a camcorder, I'm just using it for backups and stuff.)

---

