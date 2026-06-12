---
title: "Can't write to External hard drive ???"
date: 2008-01-12
forum: General Help
---

### Post by thenetduck on 2008-01-12
All the sudden I can't write to my external hard drive. Why does this happen? It could just a couple days ago and I haven't changed anything with permissions or like that. This is weird. 

The Net Duck

---

### Post by deejross on 2008-01-12
Can you read stuff on the drive, or is it completely inaccessible? Does it work again if you unplug and plug it back in?

Ross

---

### Post by thenetduck on 2008-01-12
I can read it ... but I can't write to it. I have turned it on and off with the same results. I have even tried reformatting it to ext3 and now I am back to resierfs Still can't write to it. I can read files just fine however. 

the net duck

---

### Post by deejross on 2008-01-12
Strange indeed. I know this is a stupid question, but it needs to be asked. Does the drive have a read-only switch on it somewhere that got bumped? The next thing I would check to see who the owner is and make sure the permissions are correct. And to eliminate permissions as a problem, I would format it as FAT32 and see if it still has problems. The last unthinkable option is that the drive is faulty. I have had a couple external drives go out on me after only a week of use. But let's not worry about that yet :)

Ross

---

### Post by thenetduck on 2008-01-12
Ok, 
File permisions say I can only read it and it belongs to "root" I think I need to some how add it to the media group or something like that? Owner is "root" and group is "root" 

The Net Duck

---

### Post by deejross on 2008-01-12
Try this: Go to System -> Administration -> Users and Groups. Click your name and click Properties. Then click the User Privileges and make sure your user has everything checked except "Use tape drives" and "Send and receive faxes". If everything is already checked, then just chown the drive.

---

### Post by thenetduck on 2008-01-12
It didn't work, but I got to get back to work (im on break.) I will continue trying to figure out what is wrong in about 4 hours. 

thanks Ross

---

### Post by deejross on 2008-01-12
Sure thing...I'm not sure if you tried doing a chown or not, but worst case, you can do a chmod -R 666 */path/to/drive* (or 777 if you need to run scripts from it) that way, you will always be able to write to it, regardless of who owns it.

Let me know if you need help,

Ross

---

### Post by thenetduck on 2008-01-13
Tried but still not sucess... :(

Edit... 

Got it working. I did what you said, changed it to 666 but that didn't work so I changed the owner to me.... and then right clicked on my drive, and selected permissions. Then I made sure all my file access read... "Read and Write" and my folder was create and delete files. 

Thanks all is well now. 

The Net duck

---

### Post by deejross on 2008-01-13
That's good to hear...but still, it's such a strange problem.

---

