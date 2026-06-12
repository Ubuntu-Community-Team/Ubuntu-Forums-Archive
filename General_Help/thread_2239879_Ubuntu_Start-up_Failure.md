---
title: "Ubuntu Start-up Failure"
date: 2014-08-16
forum: General Help
---

### Post by Osmund on 2014-08-16
My installation of Ubuntu 12.04 (& Gnome) fails to start up. 

 I installed 12.04 & Gnome about 18 months ago and it has worked well since. Very happy with it. Since yesterday it has failed to open.  

 Symptoms: 
 1) The Grub booter works fine (I dual boot) and launches me into Ubuntu.  
 2) Sometimes the (Ubuntu) opening process freezes before the password prompt window. More usually, but after at least 5 mins, the password prompt window opens. I enter my password and after a further 5-10 minutes it offers me a blue background (I chose this as my preferred background colour) and a movable mouse arrow but nothing more. I can get no further response.  
 3) If I return after some time of inactivity I get the password prompt window. Entering my password brings me back to the blue screen & mouse arrow.  
 4) The first time this happened I got a warning window telling me that an "applet" (as I recall) had failed ("startup.app" ? "desktop.app" ? - sorry I cant remember). Did I want to delete it? I answered no. This window has not reappeared.  
 5) I have tried opening both the Gnome & Unity desktop. Both fail similarly as described above.  
  
 I have used my installation disk to run a "virtual" version of 12.04 (“LiveCD” ?) and recovered my data from my Home folder. Also nothing visibly damaged (but then I don't think I would likely spot anything). I was not able and do not know how to get my Firefox bookmarks. This is unfortunate as they are important to me.  
  
 I understand that there is a "boot repair disk" which "is awesome but it repairs Grub only".  
 
Options:  
 1) A clean reinstall. Will work but I will loose all the additional programs and tweaks that I installed over 18 months - and I have no record (apart from my memory) of what I installed. I will also loose my Firefox bookmarks.  
 2) A 12.04 RE-install (without a re-format). But I cant see how to do this. The installation disk does not seem to offer this without re-formatting and wiping everything.  
 3) Upgrade (to 14.04 for instance) that will not delete my data and programs. But similarly I cant see how to do this from my installation disk. (I can do this from WITHIN an existing earlier version but - I can't get into mine!)  
 
 Questions:
 1) Can I get my Firefox bookmarks off my failed 12.04 installation? (I can run a "virtual" version of 12.04 to get access to the file system but don't know where to look.)
 2) Can I re-install or upgrade (option 2 & 3 above) without wiping all my programs and/or data?  
 3) Any other ideas?

---

### Post by sotiris2 on 2014-08-16
So it has trouble getting you to the login screen that's probably a major problem but when you get to the login screen, do you have an option to login as guest ? If so does it work? 

In order to save your firefox bookmarks you need to backup folder .mozilla in your home folder (press ctrl+h to show hidden files.). In order to not lose your settings you could move your whole home folder to a new partition and use "Do something else" in ubuntu installer to select that as your home partition and not format. I would install 14.04 to have a newer version. Check [this]("https://help.ubuntu.com/community/Partitioning/Home/Moving") for instructions but the commands won't work since they are to be done the installation itself and not a live usb. In sort making a new ext4 partition and putting your home folder (the one named osmund , if you use same username as in forum, not the folder actually named home) and making sure the owner is still you and not root should be ok. Then reinstall as I said above. You don't have to to anything related to fstab.

---

### Post by Osmund on 2014-08-16
Hi** sotiris2**[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1845661")
  	 	 	 	   Thanks for your reply.
 I didn't try logging on as another user. I will try that but will have to come out of my LiveCD. 
I can view the hidden folders in my Home folder but I cant see inside them because (I am using a LiveCD) and I "do not have the permissions necessary to view the contents". I also can't copy the folder or contents. Can I alter the permissions to do this?
 I have not tried it but I might have a similar problem when moving/copying the Home folder to a new partition.

---

### Post by sotiris2 on 2014-08-16
Run nautilus with sudo
```
sudo nautilus
```
If you want to save your whole home folder I suggest you use gparted to shrink your current partition to about 20-30gb and make the rest a new ext4 partition. Then put there youre home folder (which is actually named osmund) and make sure it is owned by you (it probably won't be so change it back to you. You might have to use the terminal for that.

---

