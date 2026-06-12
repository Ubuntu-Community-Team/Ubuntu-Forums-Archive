---
title: "Logging into the GDM using the command line"
date: 2007-02-04
forum: General Help
---

### Post by Kerry Lange on 2007-02-04
Can you use the command line to stop one GDM session and log into another?  If so, how would I do that?

---

### Post by amohanty on 2007-02-04
gdmflexiserver

-l will not lock existing session
-n will start anested session in the same desktop

HTH
AM

---

### Post by Kerry Lange on 2007-02-04
> **amohanty said:**
> gdmflexiserver
-l will not lock existing session
-n will start anested session in the same desktop
AM

How would I end the one existing session and start a completely new one?

---

### Post by amohanty on 2007-02-04
For that you will need to logout and restart another session. Or look at the -s option for gdmflexiserver command. I am not quite sure how that works but try it out and see if thats what you want.


HTH
AM

---

### Post by Kerry Lange on 2007-02-05
> **amohanty said:**
> For that you will need to logout and restart another session. Or look at the -s option for gdmflexiserver command. I am not quite sure how that works but try it out and see if thats what you want.

I was having a problem with Feisty.  The problem I was having had to do with logging out of the GDM.  When I tried logging out, the GDM would freeze, or at least it appeared that way.  I would get a black screen with just the "busy" cursor working away but nothing followed.

I was looking for a way to kill the "bad" session and log into a new one as a different user.  As it turned out, I was able to edit a GDM config file and reboot, which fixed the problem.

I'd still be interested in knowing how to kill a current GDM session from the command line and start a new one though.  As I understand it, "gdmflexiserver" is available only from the terminal application.

---

### Post by amohanty on 2007-02-06
Alt-F2 gives you the launch app dialog. Its kind of a terminal but more the windows run dialog.

To kill gdm from the command line just do a:

killall gdm

HTH
AM

---

### Post by bodhi.zazen on 2007-02-06
I think you will need to sudo that :)

Better yet, try

```
sudo /etc/init.d/gdm restart
```

---

### Post by Kerry Lange on 2007-02-06
Thanks for the replies!  I'll give it a try.

---

