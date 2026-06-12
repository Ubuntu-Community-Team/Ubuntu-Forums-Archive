---
title: "UBuntu 13.10  truecrypt permission issue"
date: 2014-01-15
forum: General Help
---

### Post by welefort on 2014-01-15
Im not quite sure how I did this,.

But Recently upgraded to 13.10  and I installed Truecrypt.  Logged in using my normal account, I created a new volume, and it mounted.  Basic setup nothing special.  But I dont have r/w permission to it.  Cant create folders/files.


IS 13.10 setup differently as far as permissions are concerned?  Did I miss something?

---

### Post by ajgreeny on 2014-01-15
How did you create the new volume/partition?

---

### Post by welefort on 2014-01-16
Opened TrueCrypt and selected Create New Volume,  Create a new File Container.  Selected my Hash Algorithm, entered password.  EXT4 file system.  Linux only, no files over 4 gb.  
Created.

Same way I always did it.  Worked without problems under 12.04  So Im not sure what Happened.

**Resolved.  I ended up rebooting my computer for some upgrades and now it works.  Weird.  I guess the permissions only applied after restarting for some reason.

---

### Post by berthold1 on 2014-05-25
I am having the same issue. Will try to reboot and see if it works after that.

---

### Post by berthold1 on 2014-05-25
No, rebooting did not solve the problem. The strange thing is this applies only to new volumes that I create under Ubuntu 13.10. When I open truecrypt volumes that I had created earlier, it works-I can create folders, etc.

---

### Post by berthold1 on 2014-05-25
Ok, so I found a solution that works:

cd /media/truecrypt1 
sudo chown -R $USER .as described in [http://askubuntu.com/questions/304543/truecrypt-read-only-ubuntu](http://askubuntu.com/questions/304543/truecrypt-read-only-ubuntu)

The question is: Do I have to do this every time now I mount the volume?

---

### Post by berthold1 on 2014-05-25
I dismounted and mounted the volume again-now I can create folders, so it remembers the permission change. This is weird because /media/truecrypt1 exists only as long as the volume is mounted.

---

