---
title: "How to unlock folders in ubuntu"
date: 2014-02-24
forum: General Help
---

### Post by princekrishna22 on 2014-02-24
I had Ubuntu working fine until a few days ago.
I noticed that some folders have the lock sign on them.
Now my Ubuntu is not booting so I am not able to access the drive.
So, I though I could live boot Ubuntu and access those folders.
But it says permission denied when I tried to access those folders from live-boot.

Kindly help me fix my Ubuntu boot or help me unlock those folders.
Thank you very much.

---

### Post by ajgreeny on 2014-02-24
Simply unlocking those folders may not be the solution you are looking for.

Tell us more about which folders are locked and what it is that you believe you can do by unlocking them.

If the folders are in your home, a single command should be all that is needed from recovery mode (the second boot line in the grub menu) but give us more info first.

---

### Post by princekrishna22 on 2014-02-24
Yes! It is my home folder. Like music and stuff.
I have all my homework for life in it so please tell me how to unlock it.
Note: My Ubuntu does not boot anymore and make sure your solution is using something else like using live-boot Ubuntu or something.

Thanks again!!

---

### Post by CaptainMark on 2014-02-24
Booting a live cd will work to get to those folders as long as you use root privileges, open a terminal and use either "gksu nautilus" or "pkexec nautilus" (Depending on your livecd version) and you'll be able to get access to all folders on a local drive. As to not being able to boot, have you been messing around with the chmod command? If you have then it could be a case of rescue your files and start over. If not then there could be some real evil at work.

---

### Post by ajgreeny on 2014-02-24
Try booting to recovery mode from grub, the second boot line in the grub menu, choose **Drop to root shell prompt**, then mount the filesystem as read/write with command ```
mount -o rw,remount /
``` Now run command ```
chown *-R username*:*username* /home/*username*
```Use your own username in that command.  It is possible that you will not need the leading / in /home/username as you are already in root, but I have never needed to use this way of retrieving my system so I'm not sure.  If an error says folder not found try without the leading /.
You may also need to run command ```
chmod -R 755 /home/username
```

Note that sudo is not needed for these commands when in recovery mode as you are working as root; very powerful so be careful !

---

### Post by CaptainMark on 2014-02-26
Good advice but I'm sure there is a file in the home folder that must have special permissions for you to log in, from the depths of my brain crevices I think it's .dmrc of which mine has permissions of 600

---

