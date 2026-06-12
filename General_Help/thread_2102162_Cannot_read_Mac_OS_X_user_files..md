---
title: "Cannot read Mac OS X user files."
date: 2013-01-06
forum: General Help
---

### Post by VT800C on 2013-01-06
Thank you for taking the time to read this.  

I have a 120GB SATA drive that I pulled from a Mac Powerbook that had died.  I purchased the drive case so I can use it as an external drive and try to get the files off it. I bring up UBUNTU and plug in the drive.  It's mounted automatically.  We're half-way home.

But when I navigate to the drive, and execute an 'ls -l' in the terminal window, I see the permissions of the folder I want to get to is: 
drwxr-xr-x 1  501  501 29 Aug  5  2011 [FolderName]  
I gather the user and the group is '501'. 
 
Moving on.  
Navigating into the [FolderName] folder, I see the Music folder (where I want to get the files from) is:
drwx------ 1 501 501    12 May 21  2011 Music

I have tried:
sudo chown -R [myLogin]: [FolderName]
when in the Users folder.  It asked for my password, scrolled alot of lines and did nothing.
I've also tried:
sudo chmod -R 777 Music
when in [FolderName].  
I've also tried doing the same commands from the parent folders, trying to 'push down' the changes.

I've even tried doing it through the Nautilus GUI using 'gksu nautilus'

I am out of Airspeed, Altitude and Ideas.  Is there something I should be trying?

---

