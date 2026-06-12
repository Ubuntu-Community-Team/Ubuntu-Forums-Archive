---
title: "Ubuntu 12.04 Lockdown"
date: 2013-01-18
forum: General Help
---

### Post by william_ia on 2013-01-18
Does any one know how to lock down the desktop on Ubuntu 12.04?
We are deploying pc's for public use and need them locked down so users can't change anything on them.

---

### Post by Eglefino on 2013-01-19
I'm no specialist or IT-man, but even it's another browser/platform you can ask yourself the same question. By the way, sorry for my English language (I've learned it 38-years ago ;)).

If a person have logged in than you can give every person his own rights to open the software or the program, you can read that here: [http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

Even for software on an hard-disk you can place it with a  '.' dot for the file or directory/map and it is hidden! All is most easy to use. 

Success

---

### Post by Paqman on 2013-01-19
You may want to take a look at Kubuntu. The KDE desktop it uses has a "kiosk mode" which is designed for highly locked down public computers.

---

### Post by Charles-2007 on 2013-01-22
Please look at the PDF file I posted under my user name **charles-2007** in the forum.  This is for XFCE Ubuntu i.e. Xubuntu 12.04 versioning.  I haven't been able to break what I built.  I'm not totally happy with the Firefox lockdown and am still manipulating that.

You must be logged into the forum to get the file.

Best wishes.

---

### Post by william_ia on 2013-01-23
These are all good. What I really need is the ability to lock down the user account so they can only open either Firefox or Vmware Client.
Will the permissions do this possibly? Like I said we need to lock it down that only these two things can be opened from the user side.

---

### Post by william_ia on 2013-01-29
All good idea, but does not really address the problem. We don't need to just lock applications, but the entire desktop for the user account we set up. We do not want them adding, changing or modifying anything with that desktop. In other words after it is locked down the only way to change it is to log back in on the administrator account.

Has anyone managed to be able to do this yet with Ubuntu 12.04?

Is it even possible?

---

### Post by krishnan t s k on 2013-01-29
i may be dead wrong here... but couldn&#8217;t you just create another user without administrator privileges(Standard user)? that way any modification to be made to software or files on access will require admin permissions... then again.. I&#8217;ve never really used a non administrator account so i wouldn&#8217;t know the principles on which it works
have a nice day :)

---

### Post by jbcohen on 2013-01-29
Isn't Ubuntu pretty locked down right out of the box?

---

### Post by raja.genupula on 2013-01-29
we can create a root user also . all we need to have access to Grub restore menu.

---

### Post by bantuvez on 2013-01-29
We just have to use a GRUB password to prevent this.

---

### Post by BBQdave on 2013-01-29
> **william_ia said:**
> We do not want them adding, changing or modifying anything with that desktop. In other words after it is locked down the only way to change it is to log back in on the **administrator account**.

*Guest Account* selection maybe of interest. Or create a non-admin account, regular *user account*.

Under user account, a person still would be able to tweak the browser, arrange it with tabs as the like, browser history and searches would be saved.

---

### Post by william_ia on 2013-01-29
We are using a created account. But the user can still access turned off items through the Dash Home. 
We also have an admin account. Our problem is all we want them being able to use is either _Firefox Web Browser_ or _Vmware View Clien_t. Like I said its needs to be pretty locked down. Anyone with basic knowledge of Ubuntu can get around just turning applications off in the menu. We need those (all other basic applications disabled) so the above options are all that anyone without admin privileges can access.

From my research this has been a problem for others as well.

---

### Post by bantuvez on 2013-01-29
Maybe i don't understand your question, but why don't just change the permissions on the files in the /usr/bin library or in the /usr/share/applications directory so that ordinary users won't even have read access to those files? I'm a noob here but for me this looks like a simple solution.

---

### Post by william_ia on 2013-02-01
That is the problem. Ubunutu 12.04 allows any installed program to be run from the dash home even if it is removed from the menu. That is what we are trying to prevent.
On Ubuntu 10.10 we had to actually un-install the applications we didn't want.
Be nice if something like webmin ran on the PC version to turn off or disable applications.
From what I have read webmin is only a server application.

---

### Post by william_ia on 2013-02-01
> **bantuvez said:**
> Maybe i don't understand your question, but why don't just change the permissions on the files in the /usr/bin library or in the /usr/share/applications directory so that ordinary users won't even have read access to those files? I'm a noob here but for me this looks like a simple solution.


Well that would work, but we would have do each individual directory on each machine we are setting up. With a possible 300-400 + towers that is a lot of extra work we are trying to avoid.

---

### Post by bantuvez on 2013-02-02
> **william_ia said:**
> That is the problem. Ubunutu 12.04 allows any installed program to be run from the dash home even if it is removed from the menu. That is what we are trying to prevent.


If you just want those applications to not show up in the dash, then you  only have to modify the .desktop files of those applications in the /usr/share/applications directory.  Just put this line into those files:

```
NoDisplay=true
```It's easy to write a script for this job.

---

### Post by Charles-2007 on 2013-02-05
>>>We don't need to just lock applications, but the entire desktop for the user account we set up. We do not want them adding, changing or modifying anything with that desktop. In other words after it is locked down the only way to change it is to log back in on the administrator account.<<<

Exactly.  Take a look at the howto under my forum ID (you can try the install if you have a spare machine -- I have a room full of kids trying to hack it unsuccessfully).

This assumes you are locking down one single machine.  You can create and lock down multiple users with their own logins on one machine this way pretty easily with NO extra tools.

I don't like how Firefox gets restrictions.  I have dumped it and switched to Chromium which is very easier.

---

### Post by Sternfan on 2013-05-07
Charles-2007 - I can't find your howto.

---

### Post by greatsirkain on 2013-05-07
suppose it depends on how functional you want each terminal to be, how close together they are and their purpose? Maybe look into network booting if it's feasible. Oooo flash drives, instead of hard drives, with Ubuntu live on, then you only have the guest account + easier to wipe & replace. Cheaper too, you could get away with a 4gb drive in each pc for watching films/music/general browsing etc. Just read all the posts '300-400 + towers'...Sheesh. 
Could you do something like boot each tower from the network with a version of Ubuntu running from the RAM? Then users could do whatever they wanted and all you'd have to do to reset everything is reboot which would save you having to ever fix any software problems because you could just tell the user to turn it off and on :P

---

### Post by Charles-2007 on 2013-05-27
The updated HOWTO is here:

[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)

---

