---
title: "Running a program in terminal"
date: 2007-11-23
forum: General Help
---

### Post by william_hunter on 2007-11-23
I host a game server and have always started up the game host via a terminal window. The terminal window itself basically stays open the entire time, giving me a GUI of sorts to check the status of the game. Can I run the host application without a terminal if I were to call the startup command via Webmin? I guess I don't fully understand the terminal yet! 

If I can run this without the terminal I can just set up a webmin user account for some players and let them shutdown and restart the host process when it gets laggy.

---

### Post by Nunu on 2007-11-23
can't u create a launcher on the desktop. I did that for nvidia-setting, i just created a new launcher and added the **sgsu nvidia-settings** into the launcher settings option

---

### Post by william_hunter on 2007-11-23
I don't have a problem running the command if I am home, but I want to give my players access securely so they can restart the thing if needed. I would rather not give them desktop access if I can help it.

---

### Post by Nunu on 2007-11-23
Oh ok i see where you going, sorry i must have miss read your post. Basically you want them to maybe execute the command on the server through maybe a web page?

---

### Post by william_hunter on 2007-11-23
Yeah, I have a webmin server set up and I need to make sure they can do 3 things:

1. Restart the machine if needed (this is rare as it is extremely stable)
2. Kill the game application process
3. Start the game app

If I could link 2 and 3 in one command I would love it, is it possible to write a script that will do that?

Edit: I should include the info for that game host shouldn't I?

OK, here it is, just in case. The game server is run via a shell script called nwnstartup.sh. This script calls the game server process with ./nwserver

In order to stop the server, both of these need to be shut down before we can restart them for several reasons. Is it possible to script a shutdown of each of these and then a delayed start up the nwnstartup script? I am sure it is, but I know not how.

---

