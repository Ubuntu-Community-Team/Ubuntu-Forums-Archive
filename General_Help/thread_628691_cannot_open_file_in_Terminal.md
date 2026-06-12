---
title: "cannot open file in Terminal"
date: 2007-12-01
forum: General Help
---

### Post by gilloz on 2007-12-01
The file in question is  /etc/apt/sources.list.  I can open it and view it when I go by way of Places/Computer/file system/etc/apt/sources.list.  I just can't modify the file with the text editor, because it says I have no permission.  So, I went to the Terminal and signed in as Root or Administrator by entering  $sudo vi /etc/apt/sources.list.  When I do that I basically get a blank page with this written at the bottom line:  "/etc/apt/sources.list" [New Directory]

Ok, prior to all this, I was able to get in and I was making a change on a line when I accidently hit the keyboard with my elbow and the file disappeared from the screen.  When I went back to open it again I had the following message:


E325 ATTENTION
Found a swap file by the name ie "/etc/apt/.sources.list.swp"
     owned by:root dated: Sat Dec 1 06:52:34 2007
     file name: /etc/apt/sources.list
     modified:  YES
     user name: root host name:  (my computer name)
     process ID: 7064
While opening file "/etc/apt/sources.list"
     dated:  Sat Dec 1 o0:29:03 2007

(1) Another program may be editing the same file.
     If this is the case, be careful not to end up with two
     different instances of the same file when making changes.
     Quit, or continue with caution.

(2) An edit session for this file crashed.
     If this is the case, use ":Recover" or "vim -r /etc/apt/sources.list"
     to recover the changes (see ":help recovery").
     If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
     to avoid this message.
     "/etc/apt/sources.list" 55 lines, 3050 characters

I have tried Step 2 above and I still get this same message.  After powering my computer down for an hour, I came back and now I cannot open this file in Terminal.  Don't know where else to look for help on this.  BTW, there is another file in /apt called sources.list.save which appears to be the same file.  Any help or suggestions would be appreciated.  I was modifyiing this file because I was trying to get my DVD to play and this is the suggestion that was given to make this work, by modifying this file.

---

### Post by mikewhatever on 2007-12-01
If you can open the sources list from the file browser, simply do it with root privileges. alt+F2, gksudo nautilus, navigate to sources.list, and open it with gedit text editor. You should have permissions to modify and save it.

---

