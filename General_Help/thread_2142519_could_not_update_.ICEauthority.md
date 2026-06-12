---
title: "could not update .ICEauthority"
date: 2013-05-06
forum: General Help
---

### Post by Karelio on 2013-05-06
I'm still a new user to ubuntu. 
i have version 13.04 (i just updated thinking that might solve the problem) and EVERY time i try to log on my admin  it pops up with
 "could not update .ICEauthority home/voda/.ICEauthority"
 as its loading the desktop and after it pops up, it immediately stops and puts me back at the login screen.
It won't let me on my admin login AT ALL.
I can still use the console and sudoing works fine as well.
Right now it only lets me log on through the guest.
I cant access any of the files from my admin unless in the console.
And i don't have windows on this computer anymore or i would have uninstalled and reinstalled ubuntu since I don't know how to do reboots without the dell CD

I'm not sure if i encrypted the file system when i installed or not. 
I've tryed both "sudo chown voda:voda .ICEauthority" "sudo chown -R voda:voda /home/voda/.ICEauthority" 
the .ICEauthority file was changed but it still won't let me log on.

I read something about a .Xauthority as well but it also shows the same permissions on it????
None of these other posts seem to really solve the problem
 and I dont want to just go from post to post trying different key commands since i might mess the computer up entirely.

........
SOLVED IT  I WENT INTO USER ACCOUNTS AND CREATED A NEW USER AND DELETED THE OLD ONE AND IT ALLOWED ME TO KEEP MY FILES AS WELL
I WOULD ASK HOW TO MARK THIS AS SOLVED BUT NOBODY IS RESPONDING TO ME SO.....
THANK YOU FOR RESPONDING TO MY POST NOBODY..... I APPRECIATE THE HELP!

---

