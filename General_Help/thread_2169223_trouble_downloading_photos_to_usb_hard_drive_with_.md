---
title: "trouble downloading photos to usb hard drive with shotwell, rapid photo downloader"
date: 2013-08-21
forum: General Help
---

### Post by canon-a4-5-reams on 2013-08-21
Hi everyone,

I've been trying to get photo management software set up to copy photos from my camera to an external USB hard drive.  The hard drive already has many photos stored..

/photos/2009/07/23/IMG_0816.JPG

..this is an example of how my current images are stored on the drive and I would like to keep this arrangement.  I've tried a number of photo management applications and found that many are inflexble in the directory structure they use, shotwell and rapid photo downloader look like they should cope though.  Unfortunately however BOTH programs seem to fail in the same way.  After configuring the programs to store my photos as in the example above, they instead create this..

/2009/07/23/IMG_0816.JPG

.. i.e. both programs refuse to create directories in my "photos" directory, opting instead to start from the root directory of the drive every time.  When going back into the settings, both programs have remembered the general directory structure I asked for, but have changed the directory to start from to the root directory.

I haven't found any other instances of this problem on the web, any ideas?  I'm running Ubuntu 12.04 LTS.  It's weird that both programs do the same wrong thing!?

Thanks,

Francis

---

### Post by dlynch3 on 2013-08-21
Hi Francis, you first have to select the destination directory in Rapid Photo Downloader. You can do that that in the 3rd column of the main window, under the "To" field.  If you start Rapid Photo Downloader before destination folder is mounted, then the destination directory will be reset to the root directory, which could be the cause of the problem in your case. 

I assume you are you using version 0.4.6. If not you can install it here: [http://damonlynch.net/rapid/download.html](http://damonlynch.net/rapid/download.html)

---

### Post by canon-a4-5-reams on 2013-08-31
Hi, and thanks for the reponse.  I'm sorry to have taken so long to reply.

I have tried opening Rapid Photo Downloader after the external drive  mounts and have found that it makes no difference to the behaviour of  the program so I do not think that is the problem.

I had been settting the destination directory via File > Settings.  I had a look for the "3rd column of the main window" as you suggested and could not see it, I then realised that I was running an older version, 0.4.2 I think.  I have installed 0.4.6 now which lets you set the destination directory from the main window, but it still ends up defaulting back to the root directory of the drive as it did with the older version.

I was wondering if I had the permissions of the drive screwed up, but the root directory and my prefered destination directory are both owned by me and set to rwx for owner.

I'll have another look at it later today and see if I can think of any other possibilities..

Thanks for the help,

Francis

---

