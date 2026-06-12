---
title: "Loading Updates for Garmin Nuvi 255 with Garmin Communicator Plugin"
date: 2014-04-13
forum: General Help
---

### Post by RT236 on 2014-04-13
This worked well for me just now. Using Mint 13 / Ubuntu 12.04 'Precise Pangolin', Wine Version: 1.4-Oubuntu4.1, Windows Firefox 28.
I was able to load the Communicator Plugin from the Garmin updates website. Here is what is then key!

"On the "Drives" tab, in Wine Configuration make sure you have a Windows-style drive letter to correspond with the mount point where you intend to mount the GPS device's USB drive. I use "E:" to access "/mnt". Under the advanced options, set it as a removeable/floppy drive, not "autodetect." Source and credit to Brad = [http://bradthemad.org/tech/notes/garmin_streetpilot.php](http://bradthemad.org/tech/notes/garmin_streetpilot.php)

The Garmin site then found my Garmin Nuvi 255 and I did a system update for the Garmin following the regular directions on the Garmin website.

The catch I noticed was, I tried it again and the Garmin website could not find my device, but then I noticed I just had to go back into Wine and do as above on the "Drives" tab in Wine.

I'm passing this along in case it also works for you on this or other Garmin devices. In the past I used Virtualbox and Windows XP, but this time this other method worked, mainly, because of the info about setting the "Drives" tab for the Garmin as E: as a removable/floppy drive, and DO NOT set "autodetect".

---

