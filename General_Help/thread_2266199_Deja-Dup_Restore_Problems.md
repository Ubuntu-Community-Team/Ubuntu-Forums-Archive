---
title: "Deja-Dup Restore Problems"
date: 2015-02-20
forum: General Help
---

### Post by BlueAZ on 2015-02-20
Hello,   Yes, I've searched & read all posts about this.  Nothing is working.

Running 14.04 on AMD 4-core 64-bit 300 Gb system.  My Trusty got buggy, then locked up the other day.  I used the live 14.04 CD to get into the system & make a full backup using Deja-Dup, onto a 16 Gb USB.  Then I used said live CD to reinstall Trusty to the same HDD.  After updating & upgrading to current, I tried to restore my backup from the USB.  I have other backups, yes, but none quite up to date...

First, DD kept refusing to cooperate, so I copied the whole backup to my new Home folder & eventually was able to get DD to restore from there.  But when it was done, still no personal files in my Home folder.  I had kept DD checked to put things back in their original places.  So I restarted.  But after logging in, I just got the blank 14.04 screen; it never went to a desktop.  

Being a glutton for punishment, I reinstalled 14.04 again from the live CD, updated, upgraded, etc.  This time I was able to get DD to restore from the USB.  Watching carefully this time, I saw that as each file was restored, the list said:  /media/ubuntu/216...lots of #'s, then names of my original files.  Sure enough, afterwards there were still no personal files in my Home folder, but when I opened Media, there was a folder called Ubuntu.  But I can't open it or even see its size, as I'm told I don't have permission because I'm not the owner.  Ahem, this is me doing this the whole time...  if I don't own it, who does??!!

So I restarted again, and again after logging in I get the blank orangey screen that says ubuntu 14.04 bottom left, but no further.

What am I missing here?  And how can I resolve this situation??  Please??!!

Thank you, those who know so much more Ubuntu than I!

---

### Post by BlueAZ on 2015-02-24
Well, no responses.  Have I been unclear or offensive in my post?  If so, I'm sorry.  I'm still working on the problem.  I'd like to be able to access the files inside the backup, as I think the complete backup retained the problem that messed up my whole Ubuntu installation.  But there are files in there I still need.  At present, I'm blocked from access by root priveliges, so I will search for ways to get that access.

My conclusion from this experience is that Deja-Dup/Duplicity is not the way to go for me.  I also had a year-old backup made in BackinTime, which I was able to access.  I've got the files from that backup, which I'm grateful for.  All I had to do was install BackinTime, and it opened the backup easily.

Thanks as always for any input!

---

### Post by deadflowr on 2015-02-24
When you say you made a full backup, does that mean full system backup, including non-home folder folders, like those for /usr, and /etc?

---

### Post by QIII on 2015-02-24
Hello!

No need to wait three days to bump your thread.  Remember that the forum community is comprised of volunteers around the world.  Your thread may have gotten buried before just the right person saw it.

We have relaxed the 24 hour bump restriction.  A bump after 12 hours is a reasonable way to bring your thread to the attention of an entirely different group of people in other time zones.

Cheers!

---

### Post by BlueAZ on 2015-02-24
Thank you!  In response to deadflwr, I made a full backup per the choice given me by Defa-Dup.  I did not use the terminal, I used the DD interface.

Update:  I had forgotten how to use gksu nautilus.  I'm almost 65 now, and I do forget things ;~}   I have used the terminal to initiate gksu nautilus.  From there, I was able to open the partition where I had stored the DD backup, safely away from my working boot partition.  I was then able to open the DD file and get into individual files.  I found the things I wanted and moved to Desktop, so I could go through them further.  Then I closed the Terminal, even though it said it was still running a process.  Now there is nothing on my Ubuntu Desktop.
Agggghhh!  Where are the files??  And have I blundered into a state of being in root still?  Now I really need some help!!

---

### Post by deadflowr on 2015-02-24
I'm not sure, but I'm guessing it might have been moved around (at some point) as root owned.
Something like the .Xauthority file being owned by root can cause a login-loop.
(Files and Folder in your home folder need to be owned by you, mainly --exceptions being files and folders you set permissions to be owned by users other than yourself; but you would have to have done so willingly.)

Also, when you run gksu nautilus it opens in the /root home folder and not your users home folder, so the files are most likely in there instead.Try re-running the gksu command and see if that is the case.
If so, try moving it into /home/you.
(Go to the left side pane "Computer" to help navigate the file system)

(Extra caveat --after you move the folders and files into the right home folder/directory right click on them and change the owner in the permission tab. You can do this while still in gksu nautilus.
You should be able to do this on the top-level ;eg, right click on the home folder for your user)

I feel like I'm confusing myself, so I hope it makes a little sense to you...

---

### Post by BlueAZ on 2015-02-24
OK, I've found the files.  I have to go into gksu nautilus, and they're in that Desktop.  I was able to copy one onto my main Ubuntu desktop, but it's locked.  I can only open it when in root.  And I can't remember how to exit root, which is important.  I will search for that answer.  How can I get the files & folders I've rescued into my regular Home folder, in non-root access mode?
Thanks!

And to clarify, with the folder I've managed to move to my Ubuntu desktop, when I go into properties and open Permissions, it says Root and I can't change it.

---

### Post by deadflowr on 2015-02-24
> **BlueAZ said:**
> And to clarify, with the folder I've managed to move to my Ubuntu desktop, when I go into properties and open Permissions, it says Root and I can't change it.
 From pure/normal nautilus or from gsku nautilus?

---

### Post by BlueAZ on 2015-02-24
Well, I got confused, as I didn't know if I was still in root or not.  I've opened my terminal from my regular desktop and the name is my normal name, not root@....   So I take it that I'm not in root now, right?   When I open the folder on the desktop, I'm in gksu nautilus.  But when I right-click and go to properties, permissions, it still says root; you can't change permissions.
Hope that's clear.
Thanks!

---

### Post by deadflowr on 2015-02-24
Perhaps a recap of all that is happening and/or happened is in order.
I think it's gotten a little confusing.
As I'm not sure which backup(s) is(are) involved, and I'm not sure where everything is.

*(Or, everything makes total sense and I simply cannot grasp it anymore; could happen)
But I'd hate to move with any advice which may cause even more confusion, as it where.

---

### Post by BlueAZ on 2015-02-24
OK, but another update:  I've been able to transfer the files I wanted from root nautilus to my Ubuntu Home Folder!!  It really helped that you mentioned going into Computer and finding that Home Folder.  I also figured out that a simple 'quit' in the terminal closes root.  So much of the original problem is solved!!  Yay!!!!!

The only remaining quirk is that the folders I've transferred to Home still have a little lock on them.  I can open them, but can't move/copy things to and from them.  I'm guessing that if I go back into gksu nautilus, I can navigate into my Home Folder and change the permissions.  Don't have time now, but will try that later and report.

Thank you so much!!  Ubuntu ROCKS!!!

---

### Post by BlueAZ on 2015-02-26
Final Update:  I was able to change permissions by using gdsu nautilus, and to copy/move individual files and folders from the deja-dup backup to my Home Folder.  I still had to use gksu nautilus to change permissions on some of those folders to make them fully accessable.  But I was able to get the stuff I wanted without restoring the full backup which had apparently captured the system-crashing problem.
I will probably not use deja-dup again, as this whole process was annoying and time-consuming.  I like BackInTime much better, and will use it instead.
Hope this helps someone else!

---

