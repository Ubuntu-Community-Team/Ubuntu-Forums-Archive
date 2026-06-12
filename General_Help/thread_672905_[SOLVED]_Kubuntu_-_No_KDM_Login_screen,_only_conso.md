---
title: "[SOLVED] Kubuntu - No KDM Login screen, only console"
date: 2008-01-20
forum: General Help
---

### Post by alingham on 2008-01-20
For the last little while I was having trouble with logging into Kubuntu gutsy with the old 'kinit: no image' bug.
I've managed to fix this, but still end up having a console login screen when I start up the machine.
No errors are displayed, I can login and then do a 'startx' in the console and away we go, no problems, but this is neither ideal nor aesthetically pleasing for my artistic eye. It also leaves me with only having the graphical "log out" option instead of restart, shutdown etc...
I've searched forums and google high and low. No one else seems to have this problem.
Being the Linux amateur I am, I haven't got the foggiest of where to start or what is actually wrong - because as I say, there are no visible error messages!  

Help! Please...?

---

### Post by ajgreeny on 2008-01-20
Perhaps worth trying to reinstall kdm, and then do ```
sudo dpkg-reconfigure kdm
```It may help, but if not it sounds as if you need to ensure that kdm actually starts at bootup.  Have a look to see if the script file **kdm** is in your **/etc/init.d** folder.  If not you need to make sure it is, but unfortunately I cant remember exactly how to do that.

Anyone--?

EDIT
After reinstalling kdm, if you have done so, try the command ```
sudo /etc/init.d/kdm start
```which may do the trick for you.

---

### Post by alingham on 2008-01-20
Thanking You!
Worked like a charm! I did the first bit but didn't see your edit. 
Without the edit the login screen works, but then reverts back to a console login...

Thanks heaps! Problem solved!

---

