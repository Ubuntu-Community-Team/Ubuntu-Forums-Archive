---
title: "Backup Scheme Help"
date: 2008-06-17
forum: General Help
---

### Post by nighthawk98tj on 2008-06-17
Good Evening,

I am in the process of setting up a backup scheme where my desktop and laptop PCs use rsync to backup over the LAN to my Ubuntu server.  This part of the project is all functioning properly now, but the problem I am having is with the second part of the project...

I am trying to setup my server to rsync all of the backups to a USB HDD (Western Digital Passport 60 GB).  Unfortunately, my server is having serious issues with the hard drive and does not want to transfer files over to it for more than a few minutes before it freezes up and has to be rebooted.  I've worked on it for a while and have come down to it being an issue in the ehci driver (some others are having the same issue) and I've been unable to fix it.

My workaround idea has been to use rsync to pull or push the files over the network to my laptop with the USB HDD connected to it.  I think this will only work if I push them as I would need to be root on the server to push some of the system file backups to the laptop.  I think pulling them from the server to the laptop with my user would fail when reading some of the files on the server.

I'm essentially looking for other suggestions as this just seems inefficient to me... to backup the laptop to the server, then back up the backups from the server, across the network, to the laptop and onto a USB hard drive...  Does anyone have any suggestions as to how to set up these remote backups and get around any permissions problems while not having functioning USB drive support on the server?

Anything is appreciated.

Thank you!

Tim

---

