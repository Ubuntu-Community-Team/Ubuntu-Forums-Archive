---
title: "Messed up permissions"
date: 2015-10-23
forum: General Help
---

### Post by ra-p on 2015-10-23
Hi

I think i messed up the permission of my ubuntu server by mistake. 
I run something like: sudo chmod -R 655 /.

Now everytime I use the sudo command I get the following error:
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set

Is there any way I can fix the issue by ssh? Unfortunately since it is a hosted server I have no direct access to it to run recovery mode or similar.

Any help would be very appreciated.

Thanks.

---

### Post by TheFu on 2015-10-23
Bad news.  File and directory permissions and both owner and group ownership a central to Unix security.  You've hosed your system.  Completely.  There are choices.
a) restore from a backup which maintained the correct permissions
b) copy off whatever data you must have, reload the OS, copy the data back where it was, being very careful about the owner, group and permissions.

In the future, don't type commands without an understanding of the consequences. 
Unix does whatever you tell it to do. YOU are smarter than the software, that is the assumption.
My best suggestions for learning Linux: [http://blog.jdpfu.com/search/?q=learning+linux](http://blog.jdpfu.com/search/?q=learning+linux)

Good luck.

---

### Post by ajgreeny on 2015-10-23
Sorry to say this but TheFu has got it totally correct; you have messed up the OS of the server beyond any practical chance of redemption.

The files and folders in the root (/) partition have, by default, many different permissions set, and if you change them *en-masse* in the way you have done there is no way back (that I'm aware of), and even if there were it would probably take so long as to make it totally uneconomic to try.

Just out of interest, why did you run that command; where did you see it suggested?  It would be worth trying to get it removed, if that were an option, if we know where you saw it, but if you simply edited a similar command you had seen somewhere in the hope that it would do something useful for you, this will, I feel, be a hard lesson learned.

---

### Post by ra-p on 2015-10-23
Thanks a lot for your feedbacks.
As you for sure realized, I'm not that familiar with linux commands yet. What I actually intended to do is to set the permission for all files in the current folder, but i misspelled "./" as "/."
As you said ajgreeny "hard lesson learned" ;)

---

