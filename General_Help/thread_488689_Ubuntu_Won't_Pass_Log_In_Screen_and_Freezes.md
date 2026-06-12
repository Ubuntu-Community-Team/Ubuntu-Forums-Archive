---
title: "Ubuntu Won't Pass Log In Screen and Freezes"
date: 2007-06-30
forum: General Help
---

### Post by raashell on 2007-06-30
***FIXED***

I recently switched from XP to Ubuntu Fiesty Fawn.  Yesterday, I turned off my computer, and when I went to turn it on this morning it wouldn't pass the log in screen.  I enter the log in name and password, hit enter, and the screen goes to a blank Ubuntu background and then a few seconds later a white square appears in the upper left corner.

  The Nautilus manager does not start up.  I suspect that the freeze has something to do with alterations I made to network related *stuff*  previously, in an attempt to get my Innotek Virtual Box (Windows) to network with my host Ubuntu computer, but do not know for certain.

  Update:

  I ended up waiting for five minutes and the desktop eventually came through, with this message:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, _or the network connection was broken._

GNOME will still try to restart the Settings Daemon next time you log in."

***WHAT I DID TO FIX IT***
  
  In trying to get my Innotek Virtual Box Windows Machine to network with Ubuntu, I went through a list of instructions pulled off the internet to reconfigure my computer.  The reconfiguration did NOT work and eventually I found another way (guest additions iso which comes with the program, you just have to figure out where to find it).  During this time, I hadn't rebooted, and when I eventually did, Ubuntu tried to run my altered  /etc/network/interfaces file and could not, because I had mangled it.  Fortunately, I had saved an unaltered copy on my desktop and replaced the damaged one in this file folder.  Once I rebooted, everything was gravy again.  Hope this helps anyone who might have made the same mistake.

---

