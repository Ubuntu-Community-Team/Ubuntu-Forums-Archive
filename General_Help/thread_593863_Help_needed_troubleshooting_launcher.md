---
title: "Help needed troubleshooting launcher"
date: 2007-10-27
forum: General Help
---

### Post by kokaku on 2007-10-27
I am trying to create a Launcher for Jetbrains IDEA Java IDE.
I've tried Application and Application in Terminal pointing to the idea.sh
Neither one works (the former does nothing, the latter briefly flashes a terminal that disappears).

I can run the application from a terminal without problem.

This seems like it should be a simple thing and yet it does not work.

I read other threads on this and found nothing that helps. I also posted to Absolute Beginner Talk and got no response. 

Any ideas for running IDEA or at least how to troubleshoot the problem?

Thx
andy

---

### Post by smartboyathome on 2007-10-27
run "idea.sh && ", perhaps? I think that should keep the terminal open and tell you the error. Also, if this just prints text in the terminal, it won't stay open, you have to run it and make it stay open (you can use an infinate loop to do this).

---

### Post by kokaku on 2007-10-27
No luck with that. I have other launchers that do work so it must be something about the shell script itself that isn't working. Does the launcher have a debug mode?

---

