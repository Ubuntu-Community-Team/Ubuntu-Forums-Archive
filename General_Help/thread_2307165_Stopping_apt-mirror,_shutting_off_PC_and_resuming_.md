---
title: "Stopping apt-mirror, shutting off PC and resuming later???"
date: 2015-12-22
forum: General Help
---

### Post by DVD-R on 2015-12-22
I've setup apt-mirror to download a repository.
I started it this morning, just to verify it can work.
I was connected to a DSL internet connection at the time, so downloading 40 GIG would take a long time at 180kb/s
When I started it, it looked like it was working fine, downloading the index files etc.
But I had to shut the PC down and leave.

I have an opportunity to utilize a high-speed internet connection at a friends place.
So I want to restart the process there.

I'm not sure if apt-mirror is designed for stopping \ shutting down \ and restarting again.
Does anyone know if apt-mirror can function that way?

I know that there is a file that apt-mirror creates called a lock file  /etc/apt/mirror.lock
If all else fails, I suspect I can remove that file and start over.
Any suggestions, hints or tips from apt-mirror users on the business of restarting the PC in-between processes would be greatly appreciated.
Thanks in advance :-]

---

### Post by sandyd on 2015-12-22
Partial downloads are stored in a temporary directory and are resumed when it it run again, just like in APT.
It will perform integrity checks, so you will not get corrupt downloads.

---

### Post by matt_symes on 2015-12-22
Hi

> **DVD-R said:**
> I'm not sure if apt-mirror is designed for stopping \ shutting down \ and restarting again.
Does anyone know if apt-mirror can function that way?

I know that there is a file that apt-mirror creates called a lock file  /etc/apt/mirror.lock
If all else fails, I suspect I can remove that file and start over.
Any suggestions, hints or tips from apt-mirror users on the business of restarting the PC in-between processes would be greatly appreciated.
Thanks in advance :-]

apt-mirror can continue downloading so there's no problem there. Just ctrl C to stop it.

Just re-run the apt-mirror command and pass in your mirror list as usual. It will download the sources list again and continue where it left off.

I once downloaded most of the standard Ubuntu repositories which took ages and was ~120Gb in size.

I had to run a post script download script to set every thing up correctly IIRC.

The just set up apache to serve as a local repository.

You can re-run the apt-mirror command again to re-sync the repositories when they get out of sync.

Kind regards

---

### Post by DVD-R on 2015-12-22
Wonderful!!!
Thanks very much Sandyd and Matt_symes!!!
Many thanks :-]   
A very happy guy! :-D

---

### Post by matt_symes on 2015-12-22
Hi

> **DVD-R said:**
> Wonderful!!!
Thanks very much Sandyd and Matt_symes!!!
Many thanks :-]   
A very happy guy! :-D

No worries :)

Just to let you know, i had to run a postmirror script to wget the Release, sources.gz and sources.bz2 and put them into the correct directories so the mirror would work when served by apache2.

I don't know why i needed to do this, but i did. I never investigated why this happened, i only looked to see what was downloaded and wrote the postmirror script to fix it.

If this happens to you then PM me on these forums. 

PM me, as i'm not always on the forums and sometimes need to spend weeks away (much to my chagrin), and, if you PM me, i'll get an E-mail notification for the PM.

Kind regards

---

