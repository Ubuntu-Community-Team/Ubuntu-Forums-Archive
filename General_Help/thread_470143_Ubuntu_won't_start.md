---
title: "Ubuntu won't start"
date: 2007-06-10
forum: General Help
---

### Post by Ronius on 2007-06-10
Hi all,

Ubuntu doesn't appear to start. Or rather, I should probably say it boots fine, but doesn't seem to load the window manager. I just seem to be staring at a mouse pointer kindly indicating to me something is loading. For an eternity.

I openly admit I have been extremely liberal in my usage of Synaptic Package Manager in the last couple of days; downloading packages for new splash screens and log in screens and themes and the like.

Had this been a Windows installation I would have taken this opportunity to nuke the entire system and start from scratch. I'm intriuged in fiddling under the bonnet to get this working again, however.

Does anyone have any suggestions? My plan was to just nuke the GDM packages and reinstall them, however I am not 100% sure how to use apt-get or aptitude to uninstall and reinstall the files. I am also having problems with my CD-RW and was planning on doing the same with packages relating to this device, however am not sure what packages I should reinstall.

Alternatively, at the very least is there a way I can save my system with the Ubuntu installation CD? All I really want at the very least is to make sure I can get to all the files I've downloaded.

Thanks a lot,

Watty

---

### Post by MikeDX on 2007-06-10
If you can get to a shell, then 
sudo dpkg-reconfigure xorg

may fix X for you.. if that is of course what is wrong.

You may also try killing your session config files from your home directory, or better yet if you can setup a new user to see if it is your session stuff that is stuffed.

I cant be of any great help, I'm still learning!

---

### Post by Ronius on 2007-06-10
Hey MikeDX,

I booted into recovery mode and tried what you suggested but it didn't seem to work. I'm just about to try the LiveCD and fiddle around with that. I'm not sure that creating a new user will make a difference, the problem starts before the Login Screen comes up.

Thanks for your suggestions though!

---

