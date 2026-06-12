---
title: "Apport error after update"
date: 2013-03-21
forum: General Help
---

### Post by afrimax on 2013-03-21
Greetings:

Last night I updated (not upgraded) my Ubuntu 12.04 machine as per suggestion from the update manager (I do so regularly without even reading the details) and then went to bed. Today my machine is not working.

After logging in, the menu bar flashes in and out of visibility before it disappears altogether. The entire screen flashes black and back a few times and I also get a pop up dialogue box reading "System program problem detected" as the title, and text "Do you want to report the problem now?"

In a matter of minutes, the machine is not longer functional. The mouse can move, but everything else is frozen, including the system clock (when I can see it). I have searched the forums and tried sudo rm /var/crash/*. That has bought me some time, but has not even come close to fixing the problem. I have filed reports but those just send me back to the forums or the machine becomes unresponsive before then.

HELP!

- Max

---

### Post by Gonzogardener on 2013-03-22
Yes, I am getting this as well. I have gone from 12.04 (frozen Desktop) to 12.10 and bck to 12.04 (using the old kernel 3.2.0-23 from my installation disc.

Is this some sort of a virus? Or a hardware issue?

Gordon

---

### Post by afrimax on 2013-03-22
> **Gonzogardener said:**
> Yes, I am getting this as well. I have gone from 12.04 (frozen Desktop) to 12.10 and bck to 12.04 (using the old kernel 3.2.0-23 from my installation disc.

Is this some sort of a virus? Or a hardware issue?

Gordon

I have gotten rid of the pop up error messages, but I still get the frozen desktop (the mouse still works) after a few minutes being logged in. I am about to revert back myself. 

It does look just like a virus, but I have no idea what to do.

---

### Post by afrimax on 2013-03-22
It seems that I have found the problem and a temporary patch.

It looks like Ubuntu One is causing the system freeze. I suspected that was the case, so as soon as I log in, I start up the system monitor, go to processes and then disable the two Ubuntu One processes (starter and synching). The system has not frozen since.

The problem, obviously, is that I no longer have the benefits of Ubuntu One, but at least I can work today and figure out this problem later.

Let me know if this works for you.

---

