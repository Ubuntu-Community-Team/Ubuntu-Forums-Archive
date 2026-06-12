---
title: "Ubuntu VNC server gray screen"
date: 2014-09-24
forum: General Help
---

### Post by CarryOn on 2014-09-24
Hello,
There was a thread previously, called [SOLVED] [Ubuntu Server VNC Server - Gray Screen]("http://ubuntuforums.org/showthread.php?t=1707906")
I tried the proposed solutions offered there but unfortunately that did not resolve my issue. 

We have a Ubuntu server (Xwindows). 
Used a Mac, terminal window, to access the port. 

Downloaded a free trial for Real VNC for the Mac.  Used that VNC Viewer to log on to the server. (It expires next week, and then, I don't know what I'll do, 
but that is another issue.)

No problems on that first day using the VNC. 

On a second day, logged on again.
Now there is a gray window, with no "applications menu" and no icon to take me to "terminal emulator". 
The connectivity screen for Virtual Mode is open; I can use the "more" button to look at options, but even though the Hide button appears to be operational, 
nothing at all happens when I click on Hide. 

So, I have no functionality.  Would someone be able to advise me on how to restore functionality to the VNC desktop?

Here are the steps I have tried so far:


The .xstarter file is identical to the one in the other user's account. (We had changed from gnome to Xwindows). 
The permissions are set up the same way in both accounts.

I looked into the *.log file and found this error message:

error opening security policy file  usr/X11R6/lib/X11/Xserver SecurityPolicy
Could not init font path element built-ins. Removing from list !


Using someone else's account, I went into the system and became a superuser. 

I located etc/X11/xinit/xinitrc
Permissions were set to    
-rw-   r - -   r - -
I changed this to 
-rwx  -r - - -r - -

exit/ logon as myself/ same problem


Then I located my .Xauthority file;  the permissions were   -rw -    -r - -  -r - -   myname   myname
Another user (who has no problem with VNC) has similar permissions in her account.   
Therefore, I did not change this.


Any help would be much appreciated. Thank you.

---

### Post by CarryOn on 2014-09-26
Hello, 
I am replying to my own post. I am very happy to report that this problem has been resolved.
I 'killed' and re-established the connection. So easy!     Stay calm and.......

---

