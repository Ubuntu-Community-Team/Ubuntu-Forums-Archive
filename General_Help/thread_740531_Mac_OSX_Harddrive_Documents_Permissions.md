---
title: "Mac OSX Harddrive Documents Permissions"
date: 2008-03-30
forum: General Help
---

### Post by user481516 on 2008-03-30
I have a fairly complicated situation here that has really thrown me for a loop.

A while back my old iMac G3 had a HD attack and wouldn't boot up.  

Most of my picture and music collections were on the OSX partition.  

I have the HD hooked up to my PC now and I mounted it in Ubuntu Gutsy.

I can access the HD and some information.

The problem I have is that all of the files in the user/.../pictures(music) folders are inaccessible because I 'don't have permissions'.

Is there any way to override the permissions to get my data back?

Can I prove to Ubuntu that I am the owner and I have the username and password?

I don't have a Mac computer to hook it up to as a secondary because it's an iMac.

[Here is a screenshot of what I get when I mount the drive.]("http://www.panoramio.com/photos/original/8990692.jpg")

---

### Post by gobbles414 on 2008-03-31
> **briantadhorrocks said:**
> I have a fairly complicated situation here that has really thrown me for a loop.

A while back my old iMac G3 had a HD attack and wouldn't boot up.  

Most of my picture and music collections were on the OSX partition.  

I have the HD hooked up to my PC now and I mounted it in Ubuntu Gutsy.

I can access the HD and some information.

The problem I have is that all of the files in the user/.../pictures(music) folders are inaccessible because I 'don't have permissions'.

Is there any way to override the permissions to get my data back?

Can I prove to Ubuntu that I am the owner and I have the username and password?

I don't have a Mac computer to hook it up to as a secondary because it's an iMac.

[Here is a screenshot of what I get when I mount the drive.]("http://www.panoramio.com/photos/original/8990692.jpg")

I was in a similar situation when my fiancee's iBook died a couple of months ago. You can change the permissions on your Mac hard drive so that it's compatible with Ubuntu. Go *Applications => Accessories => Terminal*. Enter the following. Make sure to leave a space between the *R* and the */*. Press enter on your keyboard at the end of each line:

[I]sudo chmod 777 -R /media/YOURMACDISKNAME
sudo chown YOURUSERNAME -R /media/YOURMACDISKNAME
sudo chgrp YOURUSERNAME -R /media/YOURMACDISKNAME[/I]

Obviously, YOURUSERNAME is where you'll type your Ubuntu username and YOURMACDISKNAME is where you'll type the name of your Mac hard as shown on your Ubuntu desktop screen. That's it! Your Mac hard drive should now work flawlessly with Ubuntu. Please post if this solution works for you.

---

### Post by user481516 on 2008-03-31
> **gobbles414 said:**
> I was in a similar situation when my fiancee's iBook died a couple of months ago. You can change the permissions on your Mac hard drive so that it's compatible with Ubuntu. Go *Applications => Accessories => Terminal*. Enter the following. Make sure to leave a space between the *R* and the */*. Press enter on your keyboard at the end of each line:

[I]sudo chmod 777 -R /media/YOURMACDISKNAME
sudo chown YOURUSERNAME -R /media/YOURMACDISKNAME
sudo chgrp YOURUSERNAME -R /media/YOURMACDISKNAME[/I]

Obviously, YOURUSERNAME is where you'll type your Ubuntu username and YOURMACDISKNAME is where you'll type the name of your Mac hard as shown on your Ubuntu desktop screen. That's it! Your Mac hard drive should now work flawlessly with Ubuntu. Please post if this solution works for you.

Hey thanks a lot, I'm sure that would have worked, I ended up just logging in as root and suddenly I had access to all the files I needed.  Thanks for being the one person to respond I appreciate it.

---

### Post by gobbles414 on 2008-03-31
> **briantadhorrocks said:**
> Hey thanks a lot, I'm sure that would have worked, I ended up just logging in as root and suddenly I had access to all the files I needed.  Thanks for being the one person to respond I appreciate it.

I hate to discourage you. But, you may encounter problems with your files from your Mac once you return to your normal Ubuntu user account. You'll probably encounter similar permission issues as when you were trying to copy from the Mac hard drive to your Ubuntu PC. The same commands that I gave you earlier should still work with the files you've already transfered. But be careful! Many of the folders on your computer are not meant to be set to the permissions that I've posted! So, only modify the permissions of your Mac folders. The *-R* part of the commands tells Ubuntu to give all of the files within a given folder the needed permissions. So, I recommend that you re-login as *root* in Ubuntu and move all of your Mac files back into a single folder -- it's alright if you have sub-folders within. Please let me know if this helps.

PS: It can take people a couple of days to reply to new posts in the forums. So, I'm sure that someone would have eventually answered your question had I not done so.

EDIT: Obviously, don't use */media/YOURMACDISKNAME* this time. Use the current location of your Mac data.

---

