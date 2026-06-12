---
title: "New user, Fresh install, many problems!"
date: 2006-10-21
forum: General Help
---

### Post by Jabjabs on 2006-10-21
EDIT - Sorry I just found the beginner forum, move or delete this. Thanks.

First a little background.

Okay I'm not the newest user around I've tried Ubuntu once before but gave up since I didn't have internet and couldn't get the software required thus I waited.

Okay I just installed Ubuntu again and the problems have begun from the very moment I logged in. I've checked around before hand and these are the problems that still remain.

First off, the system won't recognize my internet connection. I've check all the network settings and it is sending a receiving packets from the modem, that said it is putting a mysterious loopback network connection above my ethernet for some reason.

That said I checked around and I have tried to install PPPoE and I ran into my second problem. It requires me to log into as a root user, the only problem it has a password on it of which I haven't input so what the heck am I meant to do?

And now is the last problem, when ever my internet is connected (not accessing any websites mind you) the system performance is EXTREMELY slow. It takes about 3 minutes to open the terminal and I can't even access the user control panel, with or without the connection in.

Help me please, I really want to get this thing running and finally get off windows. Any help will be greatly appreciated.

---

### Post by SoggyCornflake on 2006-10-21
I'm not sure I can help you all that much, but I'll give it a try

> **Jabjabs said:**
> 
First off, the system won't recognize my internet connection. I've check all the network settings and it is sending a receiving packets from the modem, that said it is putting a mysterious loopback network connection above my ethernet for some reason. 
Have you tried running the command **ifconfig** from the command line.  It should tell you what ethernet connections you have.

> That said I checked around and I have tried to install PPPoE and I ran into my second problem. It requires me to log into as a root user, the only problem it has a password on it of which I haven't input so what the heck am I meant to do?
I think you can add a password for root fairly easily by typing
**sudo passwd**
It will prompt you for a password and that should work as your root password for then on.

> And now is the last problem, when ever my internet is connected (not accessing any websites mind you) the system performance is EXTREMELY slow. It takes about 3 minutes to open the terminal and I can't even access the user control panel, with or without the connection in.


Not sure I can help you with that, but there are many great minds that lurk this forum - I expect somebody will have the answer.

---

### Post by SoggyCornflake on 2006-10-21
About the sloooowwww system response,,,  try using a process monitor program such as System Manager (a gui program) or top (a command Line program). Either one should give you an idea what process is taking all your computer's resouces.

---

