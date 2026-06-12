---
title: "Calling Emacs Fans!"
date: 2005-07-23
forum: General Help
---

### Post by RobArson on 2005-07-23
Okay, fair warning: I'm kind of a nube.

I recently downloaded emacs and have been trying to install it. I've done the "./configure" and "make install" but emacs doesn't run. When I check the area in path where emacs is supposed to be (/usr/local/bin), it turns out everything else that was supposed to be installed was successfully installed. etags and emacsclient included, BUT NO EMACS!

can anybody help me out?

Thanks a lot, 
Rob

---

### Post by dave9191 on 2005-07-23
So it sounds like you downloaded the source code. 

./configure will run and tell if you have everything you need to compile it. If it has any errors at this stage you need to fix them first. 

Next you need the "make " command. This will do the actuall compiling. If that completes without errors, then 
"sudo make install". That will copy the program into your system installation dir's.

Then you should be able to type emacs in the command line to start it. 

**An alternative** would be to get the emacs thats in the repositories and save yourself the bother of compiling it. "sudo apt-get install emacs". Or better yet use vim ;)

Hope this helps, 

Dave

---

