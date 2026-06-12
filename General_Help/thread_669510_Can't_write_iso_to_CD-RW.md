---
title: "Can't write iso to CD-RW"
date: 2008-01-16
forum: General Help
---

### Post by bkinney on 2008-01-16
I downloaded 7.10 and want to burn the iso to disc (I'm currently running 7.04).

When I right click on the download and click "Write disc" I choose the CD-RW drive and I get the following message: "Please put a disc, with at least 695.8 MiB free, into the drive.  The following disc types are supported: CD-R, CD-RW."

The problem of course is that I do have a standard CD-RW disc in the drive and have tried a blank CD-R as well.

Any ideas?

- bkinney

---

### Post by olskar on 2008-01-16
Had this problems to..dont know hos to solve it tough

---

### Post by Craigus on 2008-01-16
Standard discs are 650 Mb, although 700 Mb sizes can be easily obtained.

Are you sure that you aren't using 650 Mb discs ?

If so, install k3b with synaptic and try burning with that.

---

### Post by bkinney on 2008-01-16
Using 80 min, 700 MB discs...sorry I'm a newbie, can you provide more info on process of installing kb3, etc.?

- bkinney

---

### Post by Gina on 2008-01-16
To install **k3b** (or other app) run the **Synaptic Package Manager **from **System > Administration** menu, **Search** for **k3b,** tick the box to install it and **Apply.**  It will then be downloaded and installed and appear in the **Applications > Sound & Video** menu.  I have done just that for use with DVD-RWs (a faster device than CD if you have the facilities).

---

### Post by ahaslam on 2008-01-16
No need to add bloat, simply:
```
cdrecord image.iso
```
If that fails, sudo it. Ubuntu gets the cdrecord permissions wrong all the time. If it needed sudoing, just:
```
sudo chmod +s /usr/bin/cdrecord
```
This should also solve your initial problem ;)

---

### Post by bkinney on 2008-01-16
Thanks all...I ended up adding k3b and it worked like a charm.

7.10 installing now!

- bkinney

---

