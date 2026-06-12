---
title: "Freeze Just Before Login Screen"
date: 2006-12-09
forum: General Help
---

### Post by ColinWilliams on 2006-12-09
Hi all,

I think I seriously screwed something up.  Last weekend I tried to install a program (I think it was MySQL GUI Tools, but I'm not sure about that).  Since there wasn't an installer script and everything was already compiled, I assumed I simply needed to extract it somewhere.  The directory structure provided matched that of /usr, so I extracted the contents of the archive to /usr.  I'm guessing that wasn't a good thing to do, since my whole system promptly locked up completely, and I had to do a hard reset.  

Upon rebooting, Ubuntu progresses past the initial bootup, I get the nVidia splash, and then the basic tan background with the working cursor (little flowery thing going around in a circle).  However, it never manages to get past that.

I have reinstalled both gdm and xserver-xorg from the downloaded cache (can't seem to connect to the internet from a prompt for some reason), with no effect.  I have booted into recovery mode and manually started gdm, also with no effect.  I have replaced my custom xorg.conf file with a default.  Nothing seems to fix it.

I've run out of ideas.  Thanks,
Colin Williams

---

### Post by riven0 on 2006-12-09
> **ColinWilliams said:**
> Hi all,

I think I seriously screwed something up.  Last weekend I tried to install a program (I think it was MySQL GUI Tools, but I'm not sure about that).  Since there wasn't an installer script and everything was already compiled, I assumed I simply needed to extract it somewhere.  The directory structure provided matched that of /usr, so I extracted the contents of the archive to /usr.  I'm guessing that wasn't a good thing to do, since my whole system promptly locked up completely, and I had to do a hard reset.  


Have you tried deleting the files from the /usr directory yet?

---

### Post by ColinWilliams on 2006-12-09
No, because I don't know which files they are.  I could go through the archive and pick them out, but I'm afraid that one of the original files might have been replaced by one from the archive due to naming.

Edit:  I just went through the archive, and noted that there are a great many libraries in the /lib directory (within the archive) that I recognize as being standard libraries.  I'm guessing that the new libraries overwrote the old libraries and are now causing some incompatibility.

---

### Post by riven0 on 2006-12-09
> **ColinWilliams said:**
> 
Edit:  I just went through the archive, and noted that there are a great many libraries in the /lib directory (within the archive) that I recognize as being standard libraries.  I'm guessing that the new libraries overwrote the old libraries and are now causing some incompatibility.

If you have a liveCD, then you can replace them. Boot up the cd, make a file in your media directory:

> sudo mkdir /media/hd

mount your harddrive 

> sudo mount /dev/whatever-your-hd-is /media/hd

Then copy and replace the files from the liveCD to your mounted hd. Try to remember what you overwrote. You may have to boot back and forth a few times till you get it right.

If anyone has a better suggestion, though, feel free to add. This seems a little complicated.

---

### Post by ColinWilliams on 2006-12-09
Quick question about that...

I have live CDs for Dapper, but I've upgraded to Edgy via the internet and don't have any for the new version.  Are the old versions going to be compatible enough to boot up and re-upgrade them?

---

### Post by riven0 on 2006-12-09
> **ColinWilliams said:**
> Quick question about that...

I have live CDs for Dapper, but I've upgraded to Edgy via the internet and don't have any for the new version.  Are the old versions going to be compatible enough to boot up and re-upgrade them?

No I don't think that'll work at all. Probably will cause greater breakage. 

Okay, try this: hit **ctrl+atl+F1**. You'll should get to the terminal. Log in and try this:

> sudo apt-get update

Then:

> sudo apt-get dist-upgrade

Then reboot with 

> sudo shutdown -r now

If that still doesn't work, try 

> sudo dpkg-reconfigure xserver-xorg

Kinda grasping at straws here, have no idea if this is going to work.

---

