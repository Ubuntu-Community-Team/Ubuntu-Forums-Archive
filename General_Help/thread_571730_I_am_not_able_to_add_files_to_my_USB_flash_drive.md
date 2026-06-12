---
title: "I am not able to add files to my USB flash drive"
date: 2007-10-09
forum: General Help
---

### Post by yyz on 2007-10-09
[IMG]http://img216.imageshack.us/img216/521/screenshotpq8.png[/IMG]

As seen in the screen-shot above, the folder named 'Family Documents' has a little lock symbol beside it. 
I am not able to access this folder and I neither can add any files to my 256 MB USB flash drive.
It used to work before but in the last few weeks its giving me this problem.

I am not sure about the brand of it, all I can say it has a Kurdish map engraved in it. Its got a website engraved in it too, and also its got a G & S text.

Support is appreciated, thanks all.

yyz

---

### Post by jnorthr on 2007-10-09
it maybe a permissions issue. look at the man pages for chmod; from a terminal type:
man chmod
it should explain how to make your folder read/write/execute.

---

### Post by kic_pp on 2007-10-09
I think that you need to give another permisions to that folder.

From the screen I see that your folder is locked.

Do this :
 - Right click on the folder
 - go to tab permisions  and make permisions to read and write

That's all

---

### Post by yyz on 2007-10-10
bump

---

### Post by picopir8 on 2007-10-10
As others have posted, it is a permissions problem.


Assuming you have administrator privileges, open a terminal then type:
cd /media/usbdisk/   (or whatever the folder name of your thrumb drive is)
sudo chown -R your_user_name Family\ Documents
(you will need to type your password)

This will make you the owner of all the files/folders so you should have no problem accessing them.   If their permissions got screwed up, you may need to also do a chmod, but only do that if you still have problems because this will open up all pemissions which you probably dont want to do but its better than not being able to access the files.
chmod -R +rwx Family\ Documents

---

### Post by tgalati4 on 2007-10-10
When a flash disk gets errors on it, Linux will only mount it as READ-ONLY until the errors are cleaned up.

In a terminal, post the output of:

>dmesg | tail -30

---

### Post by yyz on 2007-10-24
Thanks to everyone who gave up their time and effort to help me on solving this problem.
I fixed the problem myself, I'm glad it doesn't exist now :)

Thank you all ;)

---

### Post by vanadium on 2007-10-24
It would be very kind from your part to tell us how you solved this problem. You have been looking here for an answer, but unfortunately did not get the specific solution: you found it yourself. Posting the solution here, you may help other people that encounter a similar problem.

---

### Post by H3retic on 2007-10-31
I have this exact same problem, and am a little worried because I rely on my drive to bring homework to and from school.

Assuming that the problem is currupted data on the usb drive, could anyone suggest a program (preferably in the ubuntu add/remove utility, I don't know how to compile) to scan the drive for errors, and fix/remove them?

Right now I'll use scandisk on a windows machine to see if it'll fix it, but an Ubuntu native solution for next time would be nice.  :)

---

