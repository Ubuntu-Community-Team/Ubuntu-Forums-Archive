---
title: "Does not mount root drive"
date: 2008-04-26
forum: General Help
---

### Post by damasta55 on 2008-04-26
Does anyone know why ubuntu does not mount the root drive which i installed windows to.  The root drive appeared when I first set up ubuntu, but once I updated everything and restarted, the root drive no longer mounts.  I want to be able to access my windows files from ubuntu, so if any knows the fix, let me know.  Thank you.

---

### Post by catalina on 2008-04-26
Hi There,

To access the Windows partition you need to go to "Places" and just click on "Home" to get the file browser to open.  Once open you need to look in the left hand of the file browser where it says "Places" and your other partition should be there.  If it is not click on "Places" and "Network" and it should bring up the various windows networks available to you on your network and on your HD.

Hope this helps!

---

### Post by joshsmith on 2008-04-26
places network is not really what you want, it wont help you looking for a local drive

run 
cat /etc/fstab
in terminal, and post the output here. that will let us know what partitions ubuntu thinks you have

oh, and have you tried booting into windows since you installed?

---

### Post by damasta55 on 2008-04-27
I think it's a glitch between vista and wubi.  Just encountered on another install on another vista computer.  Tried using ntfs configuaration tool, but the disk is not listed.  I think ubuntu does not recognize the partition.  o well w/e

---

### Post by joshsmith on 2008-04-27
you are right, wubi does do things differently.
i believe your windows drive should be in /host then. type that in the adress bar and see. (or something similar)

---

