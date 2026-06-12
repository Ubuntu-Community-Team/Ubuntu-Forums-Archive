---
title: "Trouble specifying the correct path/directory for router connected hard drive"
date: 2016-05-28
forum: General Help
---

### Post by jay30 on 2016-05-28
I have been using onedrive-d to successfully sync files from my ubuntu machine to my onedrive account in the cloud.  I am wanting to move the location of my external hard drive (where the files sit) from being connected directly to the desktop to being connected to the router (so that it can be shared).  I have connected the drive to the router successfully and all network machines can access it.  I set up access from my Ubuntu machine by setting up a connection to server and then specified the server address as 'ftp://' + ip address + volume1.  (or can setup as 'smb://...).  It now shows under my network places (in the files app) as volume1 on ip address.  And I can access it ok from my desktop.

Now I need to reconfigure my onedrive-d to tell it where my local onedrive folder will be.  You do this by entering onedrive-pref from the terminal window to setup your preferences.   One of the steps asks that I specify the path/directory where my local onedrive folder exists.  This is where I am having trouble because I cannot successfully enter the path/directory name (at least not one that it will accept as valid).  I have tried 'ftp://000.000.0.0/volume1/onedrive', 'smb://000.000.0.0/volume1/onedrive', '000.000.0.0/volume1/onedrive' among many others.  Is there another way to specify this path that might be acceptable to the onedrive-d program?  Or is there another way I could have 'mapped' the drive that would be more helpful?  Can I somehow rename the mapping or something to make it more acceptable?  Any thoughts?  Thank you.

---

