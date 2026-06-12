---
title: "CD/DVD fails to burn"
date: 2014-08-20
forum: General Help
---

### Post by SimonHGR on 2014-08-20
Hi all,

I have what I assume must be a weird problem, since the world is not on fire with the same complaints: I cannot burn a DVD disk on Ubuntu 14.04. I have two burners, one internal to a three month old laptop, and a trusty external Memorex USB device. The Memorex works just fine on my "other" computer (groan, OK, I admit it, I still have windows on a desktop for the apps that aren't available on Linux).

I've tried the burning software that's part of Nautilus, I've tried Brasero, and also xfburn. They all result in a disk that has a small (visibly) burned region near the hub, and nothing more. The disks are universally useless (and not reusable, though that's not a surprise!). When run the Nautilus burner, it hangs up calculating checksum (which I think is because it simply can't read any data back from the disk it just burned). Taking forever and just failing seems to be a hallmark of this, though of course, it destroys "yet another" blank disk with every experiment I try, and after about a dozen, I'm hoping for a more directed kind of debugging before I take any more and scrap them!

How would I even begin to work out what's going on here? I had no problem burning disks with Nautilus and Brasero in the past (with Ubuntu 12.04LTS) and cannot tell if something is incompatible with this relatively new machine (but really, with a USB, drive?? Makes no sense, does it?) or if something is broken in 14.04 (which makes no sense since the whole world would be complaining).

Help, please, this is a major headache, I'm currently forced to copy stuff onto a USB hard disk, and move it to the windows box that way for burning (networking being much slower than direct to / from disk seems to be).

Any suggestions?
TIA
Simon

---

### Post by SuperFreak on 2014-08-20
I have had problems with Brasero in the past and now use K3b without any problems. I did not realize Nautilus had a burner built into the file manager. I have never seen it


edit: K3b has a simulation mode to test whether the burn will work

---

### Post by SimonHGR on 2014-08-20
Oh, wow, that's really bizarre! I assumed since so many programs failed that there must be something wrong with the drivers, the kernel, or something to do with the hardware interfaces, but k3b has indeed worked...

Many thanks!

---

### Post by SuperFreak on 2014-08-20
Welcome

---

