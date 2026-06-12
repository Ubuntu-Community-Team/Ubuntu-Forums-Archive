---
title: "Starting vncserver with /etc/init.d"
date: 2007-03-18
forum: General Help
---

### Post by eagle63 on 2007-03-18
OK, so I've got a headless workstation running Dapper that I connect to using VNC.  (xtightvncserver to be exact)  I need to start 3 VNC sessions with different resolutions as I will oftentimes connect using different computers that have different display sizes. So, I created a really simple script that just issues the command:  "vncserver -geometry 1600x1200 -depth 16" 3 different times.  (with 3 different resolutions)  This all works fine, but I'd like to be able to auto-start it during bootup so I don't have to SSH into the box and manually run the script. 

I've tried calling the script from the rc.local file, but that does absolutely nothing.  Why, I don't know.  Following the advice of another thread somewhere on this site, I tried adding the script to /etc/init.d since that seems to be the "appropriate" way to have Ubuntu launch services at startup.  
This doesn't work either, but for different reasons.  I get the error: "vncserver: wrong type or access mode of /home/alex/.vnc" when the script attempts to get launched via /etc/init.d.  Similarly, if I type "sudo /etc/init.d/vncLauncherScript.sh" I get the same error message.  Since the script works fine outside of /etc/init.d, I'm thinking this is some type of user vs. root problem.  

Since vnc is installed as part of my user's account, and /etc/init.d is run as root, it seems like it's unable to start vnc because it's not being done as my user account.  

Is there an easy answer to this?  I know there's stuff like visudo where you can start a root access job from your user account, but I'm doing just the opposite.  thanks in advance...

---

### Post by paper0k on 2007-03-18
Into the init.d script, try to use 'su', for example:
```
su - *username* bash -c "*commands*"
```
:)

---

### Post by eagle63 on 2007-03-18
That did the trick, thanks!

---

