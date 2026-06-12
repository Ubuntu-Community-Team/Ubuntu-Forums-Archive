---
title: "Firestarter disables itself"
date: 2007-10-14
forum: General Help
---

### Post by ctoaun1 on 2007-10-14
greetings all
firewall firestarter

The firestarter Icon becomes red every few minutes. This indicates that it is off. How does one get the thing to run at startup and stay on, which is indicated by a blue Icon?
If there are ways to configure Firestarter with or without terminal commands, I would be happy to know them. _Please provide complete  commands. _Please do not give partial commands and assume that I'll know what goes before, in the middle or immediately after the command. 

Please do not take the following th wrong way, but my experience with Linux community makes it necessary to state the following:

Please do not respond with, "it's in the forums," for had I found it in a form that I could have used, I would have done so. My background is predominantly windows with very light Xandros experience and even lighter Fedora Core experience, so please, no lengthy incomprehensible soliloquies extolling the virtues of IP tables. Although I am interested in configuring stuff and terminal commands, whether true or not, I feel that a firewall is a must, and I am accustomed to firewalls always running at startup without issue.

alternatively, does anyone know of a commercially available firewall product that just works in Ubuntu. I believe that it was a posting in this forum that indicated Panda had serious flaws in 2005. 
thanks for any help

---

### Post by euler_fan on 2007-10-14
Hmmm . . . I hate to ask, but when you see it go red, is it a red circle with a black square in the center or something else (like a red circle with a lightening bolt)? Alternatively, does it stop being red when you double click the tray icon to open Firestarter?

When I leave Firestarter up I usually get a hit every few minutes where it turns red to alert me to the event. Opening firestarter from tray "clears" the alert.

However, if you're getting the tray icon going to the red circle with black square, then there is a much bigger problem.

---

### Post by Tyche on 2007-10-14
ctoaun1,

Usually I've found that the red Firestarter icon indicates that the firewall has trapped an event.  If you click on the icon, the window will come up.  Go to the Event tab, and clear the events.  The icon will turn blue again.

There is, indeed, a bug that has occurred with Firestarter dropping out (no longer being active).  This was caused by the Active connections drop down window being open. Firestarter would stop functioning and the icon would disappear about 10 minutes later. (This is also mentioned on launchpad, if you're interested)   If the window is closed, then Firestarter won't "fault" like that.  The problem may be a Firestarter problem, but this has been a work-around that has worked for me.

I hope this helps.

---

### Post by ctoaun1 on 2007-10-15
Thanks for the quick responses.  
Euler_fan wrote, ". . . I hate to ask..." The fact is that it was I who failed to provide a piece of pertinent information, so the fault was mine not yours. As such, your question was helpful as was your answer.  The system was simply providing event notices (lightning bolt through red circle) not dropping off line, black square in red circle. thanks

Tyche, thanks
I'll file this in the soon to be started "Firestarter notes" file

---

### Post by bodhi.zazen on 2007-10-16
Firestarter is a gui configuration tool and is run as root.

You should not run firestarter all time, only to configure your firewall, ip tables.

Otherwise close firestarter.

If you want to monitor traffic, do so with an alternate application, like wireshark, not firestarter.

---

