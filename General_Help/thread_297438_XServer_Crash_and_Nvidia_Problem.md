---
title: "XServer Crash and Nvidia Problem"
date: 2006-11-11
forum: General Help
---

### Post by disabled_20220313 on 2006-11-11
Morning all,

I had a bit of a bizzarre problem with my Edgy Ubuntu box the other day. I booted up to find the Xserver had broken. It seemed to have "lost" the nvidia drivers that had been installed.

As far as I know I have not changed anything to do with xserver or nvidia recently, so this seems to have happened spontaenously.

I was able to get it working again by reconfiguring it, but now it seems to be using "nv", restricted-modules, rather than Nvidia's own drivers which I had installed. This means that it's being a bit sluggish, as the graphics card is not being used properly.

According to Synaptic the nvidia-glx drivers are not installed (though they were a few days ago?!), I tried to re-install the nvidia-glx package, but Synaptic seems to want to try and remove most of my core system packages. Eg. gnome-panel, GDM, lots of very important stuff.

I have recently upgraded to Edgy from Dapper, from a clean dapper install then "gksudo update-manager -c". So I have all my docuemts backed up.

The solutions to this problem would be :

(a) Working out what happened, and correcting it
(b) Trying to force synaptic to install the nvidia drivers without removing anything
(c) Doing another clean install, as I have very recent backups to work from. 

I'm not to sure how to go about any of these except the last one, so any help would be great!

Thanks,

---

