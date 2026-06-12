---
title: "Restoring help..."
date: 2008-04-30
forum: General Help
---

### Post by Lostatsea3 on 2008-04-30
So I installed Ubuntu but unfortunately I installed it over vista. Not what I wanted to do... Now I have a external drive with it all backed up... NTFS (Or whatever) format... it was just the automatic thing when I hit backup. Can I use this to restore my computer to its original form? Including getting vista back? 

Thanks!

---

### Post by Lostatsea3 on 2008-04-30
Bump! To try and get some responces...

---

### Post by bodhi.zazen on 2008-04-30
You will have to re-install Vista and then restore your data using whatever back up application you used.

---

### Post by Lostatsea3 on 2008-04-30
So do I have to rebuy Vista???

---

### Post by Lostatsea3 on 2008-04-30
Oh and I didn't do a selective backup... the whole HD was backed up. Why would vista have been excluded?

---

### Post by bodhi.zazen on 2008-04-30
What program did you use to make the backup then ?

Run that program and restore your hard drive.

---

### Post by Lostatsea3 on 2008-04-30
Ok. Using WINE?

---

### Post by Lostatsea3 on 2008-04-30
Ok I plugged it in and it came up with "Unable to mount volume"

It said to use the force option if you dont have windows. How do I do that? It gives something to type on the command line. How?

---

### Post by Lostatsea3 on 2008-04-30
Help! Please. I really need to get back to vista. I love Ubuntu, and plan on restalling it again on the right partition... can you just help me out?

---

### Post by Lostatsea3 on 2008-04-30
Wow you all are sooo helpful... 

Well I managed to get Simpleteck to run... and the program to. But now I can't seem to find the NBF file to run the restore. I can see it when I go to my computer, and the HD. But not on the program, it doesn't show when I browse. Help? 

Sorry... im just frustrated.

---

### Post by bodhi.zazen on 2008-04-30
Well, you have not provided sufficient information.

What application and how did you make a back up ? do you have any kind of instruction manual ?

When you mentioned SimpleTech a google search yielded :

[http://www.simpletech.com/support/guides.php](http://www.simpletech.com/support/guides.php)

If that is what you are asking about, I have no idea if it runs in wine. It appears it is designed to run in Windows so if the application is running with wine \o/

The problem you may have is wine uses a fake C drive, located at ~/.wine/c_drive or ~/.wine/dosdevices/c: so I have no idea if the application will restore your partition or if it will try to write information to ~/.wine.

If it is the former, you almost certainly want to be doing this from a live CD. If it is the latter my guess is it will fail and likely take wine with it.

[http://www.simpletech.com/webspeed/webtech/enter.php](http://www.simpletech.com/webspeed/webtech/enter.php)

[http://www.simpletech.com/support/contact_support.php](http://www.simpletech.com/support/contact_support.php)

---

### Post by Lostatsea3 on 2008-04-30
Its arcsoft total backup. no manual and I did an incremental back up. Linux starts the utility to restore but it keeps freezing and is unresponsive.

---

### Post by bodhi.zazen on 2008-04-30
You probably need to first install Vista and then restore your data then. Contact your hardware manufacturer and find out how to get a restore CD.

---

