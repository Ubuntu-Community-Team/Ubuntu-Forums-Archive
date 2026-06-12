---
title: "Startup Programs Slow to Start"
date: 2007-05-05
forum: General Help
---

### Post by deniro0311 on 2007-05-05
I recently installed 7.04, and for the most part it has been great.  I do have one big problem.  My startup programs (beryl manager, network manager, power manager) are taking forever to start.  I have no idea why, because the problem started out of nowhere.  

It even causes my laptop to completely freeze sometimes.  When it freezes, it happens just after beryl finally starts, and while my wireless is trying to connect.  I know this is not much to go on to troubleshoot, but I am completely puzzled.  Any help will be much appreciated.

---

### Post by deniro0311 on 2007-05-05
Add Firestarter to the list of programs that take forever/if ever to start.

---

### Post by binki39 on 2007-05-06
I am having a similar problem. After upgrading to feisty, the startup programs I have under the session take a long time to start up. I also do not get a windows decorator around my applications during startup. I have to manually launch beryl-manager in the terminal to get the windows decorator or change windows managers. Any help would be appreciated, thanks!

---

### Post by deniro0311 on 2007-05-06
It's good to know I am not the only one having this issue.  This is really driving me nuts.  Other than that, I have absolutely loved this version of Ubuntu.  I guess I can't complain too much.

---

### Post by binki39 on 2007-05-06
hey I think i found the solution. I searched in the forums and came across this thread [http://ubuntuforums.org/showthread.php?t=432527&highlight=feisty+beryl+-starting]("http://ubuntuforums.org/showthread.php?t=432527&highlight=feisty+beryl+-starting")
Apparently what cases the slow startup are the old config files. To test whether if the old config files are the cause, create a new user account and login with it. If the new user account starts up smoothly, then proceed to move the config files in your original account into a backup folder and restart gnome. Some of the config folders to move into backup are:

any .gnome*, .gconf*, .local, and .config. Try that and restart gnome. *Note*: the arrangement of my desktop icons changed, but it is a big deal. Hope this helps!

---

### Post by deniro0311 on 2007-05-06
I logged in with the new user account it started up smoothly.  Now I am assuming by moving all these files I am going to have to reconfigure my desktop, settings, etc.

---

### Post by binki39 on 2007-05-06
yeah, apparently I have to reconfig my old desktop environment's settings. Maybe you can narrow down to which config file/files in particular is/are causing the problem and just back those up.

---

### Post by deniro0311 on 2007-05-06
What a pain in the ***.  I guess I will spending the night reconfiguring my desktop, etc.  Good job on narrowing down the problem, thanks.

---

### Post by deniro0311 on 2007-05-07
Ok, I did what you suggested.  After that, I fixed all my configurations, which didn't take as long as I thought it would.  Now all my startup programs load like they should.  Thanks for the help.  I believe I may have also found the problem, at least in my case.  When I set firestarter to load on startup the problem came back.  When I set firestarter not to load on startup the problem went away.  So if anyone has the same problem with startup programs loading slow, and you have firestarter loading at startup, disable it from load.  Now you will have to start it manually when you login.

---

