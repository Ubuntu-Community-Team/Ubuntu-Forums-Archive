---
title: "restoring"
date: 2008-05-14
forum: General Help
---

### Post by sanjeevpunj on 2008-05-14
[SOLVED]I have my backup.tgz file. How do I restore it? Where do I place this file? it is on my desktop. When I run tar xvpfz backup.tgz -c / while being in root, I get a message "no such file" and I know that it is not in the root, I am having trouble placing this file in the root. This is from a previous backup and I want to restore. This is crucial, since my backup was taken afetr I solved many problems and I dont want to loose all that!

---

### Post by Monicker on 2008-05-14
How did you create this backup file?  Also, -c is to create an archive.  Perhaps you meant -C; lower case and upper case are different options.

---

### Post by sanjeevpunj on 2008-05-14
yes i mean upper C. I created this file in a previous installation which worked fine for me for a while, and then while I was in Windows XP, I installed Partition Magic, and that messed up the grub! SO I had to reinstall from the Ubuntu liveCD again. I just want to know if I am asking a logical question at all? Can I now use that backup.tgz file to restore the OS as it was before?  By the way I managed to run that command (tar xvpfz backup.tgz -C / ) and it did something, but on rebooting I found nofile in the system! So I installed yet again from Live CD and back here to send this message! I am not trying to run that backup file again now, as I feel id doesnt make sense. I dont know if I am right in assuming this or wrong.

---

### Post by Monicker on 2008-05-14
I doubt that you will be able to get the OS exactly as it was with a tarball backup. Tools such as partimage are better for that.  You will be able to recover any configs and data that are in the backup file.  When you created the backup file, what did you specify as the directory to start at?  Do you recall the syntax you used?

---

### Post by sanjeevpunj on 2008-05-14
The syntax I used was 

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

and it gave me a backup.tgz file.

While it was on the system I never tried to restore from it, but when I had this crash,I thought it would be a good idea to try restoring from it, but that failed as I I said earlier.

I am limping back to those settings I had earlier, it is just a matter of time, but is this backup.tgz totally unusable now? 

The real question is, if you just have a backup.tgz file, and nothing else, and if you manage to boot the computer with some bootable device, and then enter a terminal window and run this backup.tgz file, could you restore the system to as it was before? If not, then I can simply delete this 1.1GB flie and forget about it.

---

