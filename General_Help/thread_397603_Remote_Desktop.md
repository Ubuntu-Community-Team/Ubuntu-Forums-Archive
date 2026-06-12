---
title: "Remote Desktop"
date: 2007-03-30
forum: General Help
---

### Post by Drate on 2007-03-30
I am an Edgy user and asking a lot of questions lately, but so far have gotten succesful replies to them all.

My current question is how to use Remote Desktop, I clicked the thingy that says to let others view and control my desktop, I even took off the password option for easy access (don't freak out I am behind a Wireless Access Point's firewall, it is both my connection to the internet AND the family LAN).  So when I went over to another computer and tried the command it said to use (vncviewer HOSTNAME:0) it said it couldn't connect to vncserver.  I tried to look up help online at the VNC homepage but had no luck.  So yeah, I turn it over to The Best Tech Support Ever, the Ubuntu community.

What do I do?

---

### Post by scxtt on 2007-03-30
are you sure that "HOSTNAME" is defined on the computer you're using the client from?  did you try it w/ the IP address of the "Remote Desktop" server?

---

### Post by Drate on 2007-03-31
I wrote HOSTNAME as a placeholder for my computer's actual host name.  I did not try an ip address, but the Remote Desktop thing under System, preferences, said to use that command to access it, with the name of mycomputer put in automatically, and even an option to e-mail the command, presumably so I could remember it when I got to the omputer i needed to use it for.

---

### Post by FakeOutdoorsman on 2007-03-31
Is your router somehow blocking the port for the Remote Desktop?

---

### Post by scxtt on 2007-03-31
if the client doesn't actually know what IP address "HOSTNAME" points to, it can't connect ... the "HOSTNAME" is just for us humans, so if you're not positive it's defined - you should use the IP address just to rule that potential problem out ...

you can add hostnames to /etc/hosts (for linux) and C:\windows\system32\drivers\etc\hosts (for windows) if you want to do it w/ hostnames ...

---

### Post by Drate on 2007-03-31
Ah, I'll look into both those possibilities....

---

