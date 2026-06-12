---
title: "Troubled Encrypted Home..."
date: 2017-04-13
forum: General Help
---

### Post by artphotodude on 2017-04-13
Have run into a bad problem.  Was trying to Chown a USB formated for OSX to share files with Mint and accidentally Chowned my whole Linux system.

So having to reinstall.

But initially was giving me the "**Could not update ICEauthority file**" error, so when through the steps to fix that and it finally booted in, but to a fresh home folder (non of my files can be seen and there is the *"Access-Your-Private-Data.desktop"* and *"README.txt" * files showing)  :?: .

Tried to go through the normal ecryptfs-recover-private routine, but it only opens the new, clean file-system.  Judging by the space on the hard-drive left, all of my stuff is still there, but I'm not sure what to do next.

Should I copy the .ecryptfs and .Private files to a new drive first?

** NOTE:  I do have the mount passphrase copied down.  Also, much of this is backed-up, but there are a fair number of files not backed-up.  What would be the next step??

*** Also, when I attempt to copy the .Private folder to a new partition, it acts like it is 400+GB when it should actually be about 90GB.

If it can't be saved, is not the end of the world, but would at least be nice to know what to try next.

Thanks for any ideas!!

---

### Post by artphotodude on 2017-04-14
A quick update... The *ecryptfs-recover-private* worked just fine when done from a live-USB.  

Also, had to open the new temp dir with **gksu caja /tmp...** and copy the files with **sudo cp -R**

 :P  :P  :P  :P

---

