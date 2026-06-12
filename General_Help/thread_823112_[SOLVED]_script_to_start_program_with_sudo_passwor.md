---
title: "[SOLVED] script to start program with sudo password"
date: 2008-06-08
forum: General Help
---

### Post by dlmoak on 2008-06-08
I want to run a script to start the gui for the lightscribe simplelabeler program.  Running the following command runs the program, but prompts for my sudo password:

/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler

What can I put before this command to pass my sudo password for me.  I'll then attach the script to an icon on the menu.  Alternatively, how do I change permissions on the directory structure shown in the command line above.  Each level requires root user.

---

### Post by dlmoak on 2008-06-10
used the chmod +s command to allow access to this one program without password.

---

