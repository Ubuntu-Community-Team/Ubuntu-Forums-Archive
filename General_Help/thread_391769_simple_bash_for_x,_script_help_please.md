---
title: "simple bash for x, script help please"
date: 2007-03-23
forum: General Help
---

### Post by sloggerkhan on 2007-03-23
I'm trying to make a bash script for feisty that swaps a preconfigured  confname.xorg.conf with the active xorg.conf and then restarts x.

What's throwing me is that on feisty,  
 /etc/init.d/gdm restart 
seems to leave my current x running. 

Is there a better way to stop my x-server and restart it?

Thanks.

---

### Post by groggyboy on 2007-03-23
the problem is you are dealing with a bug in feisty.

hitting "ctrl+alt+backspace" or running "sudo /etc/init.d/gdm restart" from X don't work as they should.  i use [a script that swaps Xorg conf files]("http://www.ubuntuforums.org/showthread.php?t=361124") as well, and under Edgy I used the command "sudo pkill Xorg" to restart it after swapping conf files.  However, that doesn't work either.  Until this feisty bug gets fixed, you'll have to do one of two things: reboot your computer every time ("sudo reboot") or manually switch out of the X session and restart it from the command line (hit "ctrl+alt+F1", log in, and *then* run "sudo /etc/init.d/gdm restart").

At least, that's what I do.  If someone has a more elegant solution, I'd love to hear it too!

---

