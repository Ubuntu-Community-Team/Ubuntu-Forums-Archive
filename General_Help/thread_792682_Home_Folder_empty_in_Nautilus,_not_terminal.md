---
title: "Home Folder empty in Nautilus, not terminal"
date: 2008-05-13
forum: General Help
---

### Post by ryanferreri on 2008-05-13
Hi All,

When I open up the Home Folder /home/ryan in Nautilus it shows up empty (0 Items, xxxGB Free at the bottom). However, I know my data is there, and if I ls /home/ryan in Terminal I can see everything there. 

Only the Home folder is affected. If I open up Music or Videos or Pictures from the Places menu, they all show up with data.

Are my permissions wrong perhaps? What are the PROPER permissions on a user's Home folder? I did chown ryan /home/ryan and that didn't do the trick. 

Thanks!

---

### Post by njparton on 2008-05-13
That's interesting, I wonder if it's a bug.  Have you tried searching launchpad?

---

### Post by ryanferreri on 2008-05-13
Yeah I searched Launchpad and I don't see anything in there that matches the symptoms. If I don't get some leads here I'll report a bug. However, I want to make sure the permissions are right before I do that.

---

### Post by sdennie on 2008-05-13
Do you have a file called ~/.hidden?  It didn't used to accept wildcards but, if you have a .hidden with "*" in it, it would show nothing in your home directory.

Edit:

Also, hit Ctrl-H in nautilus while in your home directory and see what you see.

---

### Post by ryanferreri on 2008-05-13
No there is no .hidden file in my /home/ryan

---

### Post by ryanferreri on 2008-05-13
Well folks, it looks like the problem no longer exists. I installed today's updates and rebooted and now I can see the directories. I guess I'll update the thread if it happens again.

---

### Post by mcarlson1 on 2009-02-09
I'm having the same problem Ryan described; however, rebooting doesn't change anything for me. I still can't see anything in my home folder when viewing it with Nautilus. I have no problem viewing the home folder with Terminal and viewing other folders with Nautilus.

Also, attempting to view the home folder with Terminal causes the window to lock up. I can't click on any buttons or menus except the button to close the window. When I do that I get a "File Browser is not responding" dialog box and the option to Force Quit.

No major system changes have been made since the last time I viewed my home folder with Nautilus. When I started my computer today I didn't have this problem. I added a new directory to the home folder, but no other changes. Installing updates did not fix anything either. 

Anyone have any ideas about why this is happening and what I can do?

---

### Post by drs305 on 2009-02-09
I think there is a reported bug about this or something similar in nautilus. If you have a blank CD/DVD inserted it may cause the situation you are experiencing. If you have a blank CD/DVD in your system, remove it and see if nautilus now works.

---

### Post by personjerry on 2009-02-09
I believe I have a similar problem, the solution I've 'found' is to log out and back in.

---

### Post by mcarlson1 on 2009-02-09
Logging out and then back in did not work for me, and I don't have a blank CD/DVD inserted. Thanks for the ideas though.

I did find a solution. If I move one folder out of the home folder, then it works. It doesn't matter which folder. I tried different ones. It seems that it stops working when there are more than 16 folders. Is there a limit to how many folders can be in the home folder? Should I not be putting folders there? (I'm a new Ubuntu/Linux user)

Thanks again for the help.

---

