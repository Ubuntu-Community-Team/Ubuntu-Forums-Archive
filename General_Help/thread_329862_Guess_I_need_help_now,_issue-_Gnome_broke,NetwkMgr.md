---
title: "Guess I need help now, issue- Gnome broke,NetwkMgr cause?"
date: 2007-01-02
forum: General Help
---

### Post by Atomic Dog on 2007-01-02
Well I don't often need help, but this time I can't seem to find anything searching the forum.

Here's my problem.  Gnome stops responding.

-Installed Network Manager and it starts with the session.
-Everything works on a fresh reboot UNTIL Network manager connects to a wireless router.
-Network Mgr does ask for keyring access as it is supposed to.
-Network Manager takes about 2 minutes to connect (this is a long time as it normally takes 5-10 seconds.
-When Network Manager does finally connect, nothing will open in gnome -things just won't open any longer.  The UI still allows mouse movement but just about everything else won't start/launch.  ex.  terminal will open before NM connects, but once connected terminal will not. (so I can use terminal, but not launch apps like gedit if NM has connected).
- If I logout and log back in everything works fine -this is strange.

Things I have discovered:
-Removing Network Manager allows normal startup after reboot and the system still connects to the secured wireless even though it is not enabled in Networking applet.
-Completely removing and Reinstalling Network Manager gives the same results I listed above.

I'm at a loss for what is going on.  Obviously something is happening when Network Manager finally connects upon a fresh boot, and a logout and re-login cures it.  Totally strange.  This is beyond an annoyance.  Can anybody help me troubleshoot this and get to the bottom of the problem?  I can boot, login, logoff, and login again as a workaround, but I'd like to get to the underlying problem.  Thanks in advance!

---

### Post by NGEvo on 2007-01-02
I also seem to have a similar problem after installing NM, except Gnome is next to completely destroyed :neutral: :( :(

---

### Post by Atomic Dog on 2007-01-02
Well after banging my head against the wall I discovered I unwhittingly deleted my host name,  I don't know why this would cause such flakey behavior (as in I don't know what is happening behind the gui) but adding a host name again seems to have made things all better.

---

