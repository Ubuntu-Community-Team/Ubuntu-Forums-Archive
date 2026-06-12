---
title: "Is 32GB enough?"
date: 2014-03-07
forum: General Help
---

### Post by matt69 on 2014-03-07
Hi guys,

It's my first time posting here but I wanted to get some opinions.

I'm creating a media server and I'll probably use either Ubuntu server or regular desktop Ubuntu, and I'm thinking of picking up a 32gb ssd to use as the boot drive, as they're really cheap!

I'm wondering if you guys think that's likely to be enough space for me to comfortably run the following setup:

Ubuntu
Netatalk with Bonjour for AFP sharing
Samba for Windows sharing
Mdadm for RAID control
Transmission or Deluge or some other torrent software
Bittorrent Sync for syncing the whole box to another location for backup
Plex or similar media server
Probably a few other lightweight services

I'll have a 6TB RAID 5 array for the actual data storage so this is just for running the above services.

My gut tells me 32GB will be fine for this, but I don't want to waste the money and have a small and fairly useless ssd lying around.
The other option is to just install on a 250GB HDD I have spare.

---

### Post by mikewhatever on 2014-03-07
What do you mean by the "boot drive"? It may be concluded that only the boot files will be there, in which case it's way too much. A 1BG boot partition should do the job. On the other hand, 32GB would make more sense as a system HDD. In other words, the OS would be installed there, which sounds like a good plan.

---

### Post by matt69 on 2014-03-07
Yeah it'll basically be the OS and the programs mentioned above. Like I said I thought this would be more than enough but wanted to check just in case :)

---

### Post by CaptainMark on 2014-03-09
Yeah that's more than enough, I always use about 20GB for the root partition on my desktop and even after liberally installing software have never gone over 8GB used.

---

### Post by Topsiho on 2014-03-09
I think it is more than quite enough, as on a server you should run only those applications that you *** really need and not one more ***. That means that you should run the Ubuntu server version, and not the desktop. Which means that you should be able to use the terminal to do all the management.
The mean headache you should have is how to set the firewall so that you and your users are best protected.

As illustration: for installing Ubuntu desktop, which comes with Unity and tonnes of software, you need about 5 GiB, while 10 or 15 GiB probably can be exceeded if you install enough software.

The data you want to serve is installed on the large HD, so that doesn't pose a problem.

My two pence

Topsiho

---

### Post by sam_baker2 on 2014-03-09
One of my setups is running off of a 32 gig SD card.
Complete OS & lots of software.
Runs just fine.

---

### Post by 3rdalbum on 2014-03-09
A 32 gig SSD is more expensive than you need. I have a 2.5 inch laptop hard drive as the system drive... It was cheaper then, than your SSD is now. That was about four years ago and the thing is still running.

---

