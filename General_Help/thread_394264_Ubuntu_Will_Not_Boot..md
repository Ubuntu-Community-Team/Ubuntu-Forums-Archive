---
title: "Ubuntu Will Not Boot."
date: 2007-03-26
forum: General Help
---

### Post by Dr Small on 2007-03-26
Hello, I am an Ubuntu user (or was), and today my computer will not boot.
I'll give all the details.

I had mediawiki folder in my /home/drsmall/ folder, and deleted it today.
I never deleted it from the trash can, because I forgot about it, and I booted up in Windows, and left it. I went to town today, came back (and because of my bad processor), found the computer locked up. So I shut it down by pressing the button, and booted up in Ubuntu.

I saw that my trash can had something in it, so I selected the objects and clicked delete.
The mediawiki folder wouldn't delete, because it said something about being read-only.
So, I tried "Empty Trash Can" from the File Menu, but it gave me the same error message.

So, me, thinking the computer was just ill working because it locked up in Windows and I had to shut it down, I went and rebooted. When it came to the splash screen (at bootup), it almost passed it, but then took me to a black screen, and printed this:
[http://ubuntuforums.org/attachment.php?attachmentid=28337&stc=1&d=1174947467](http://ubuntuforums.org/attachment.php?attachmentid=28337&stc=1&d=1174947467)

So, now I'm stuck with Windows, and have no clue what to do.
Somebody PLEASE help me!

Dr Small

---

### Post by Dr Small on 2007-03-26
Please, ANYBODY! It's been an hour, and I still have no idea what to do!
I need help, to get my Ubuntu back!

Dr Small

---

### Post by kidders on 2007-03-26
Hi there,

Have you tried running fsck as suggested?

Assuming you hadn't done any significant system updates between the last successful boot and the first failure, and were either using Ubuntu or had Ubuntu's filesystems mounted in Windows when your PC went dead, my guess is that your Ubuntu system has been corrupted.

If this were *my* system, I would experiment with fsck to see if it suggests anything hopeful, but I would take an image of the failed filesystem before actually making any repairs. In the event your problem is serious (or widespread), it is at least possible that automated repairs could wind up making things worse.

**Edit:** This thread seems to be referenced elsewhere in the forum. :confused: It's probably not a good idea to do that.

---

### Post by Dr Small on 2007-03-26
Yes, this thread was basically recreated over in the other ubuntu new user help section, because after waiting about 3 hours with no repy, it almost became hopeless.

But I got the problem fixed over in here:
[http://ubuntuforums.org/showthread.php?t=394375](http://ubuntuforums.org/showthread.php?t=394375)

I'm sorry for making two threads on the same thing, but sometimes it can be seen in the other place faster.

Dr Small

---

