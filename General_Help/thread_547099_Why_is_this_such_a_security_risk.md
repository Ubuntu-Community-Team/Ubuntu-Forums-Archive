---
title: "Why is this such a security risk?"
date: 2007-09-09
forum: General Help
---

### Post by phoenix96 on 2007-09-09
Oh ****, I'm planning on taking out my user password - shock, shock, horror, horror.

No, I'm not asking how to do it - I would say there are more than enough threads on here to figure that out (maybe not, in which case I will be back :)) - I'm just wandering why it is **such** a security risk.

I'm talking about a computer in a house, which will never be accessed by anyone else, and if it is, the second they see an alternate operating system they will scatter like lions when something bad happens. 

So, physically in the realm of real life, there's not much of a security risk. Am I missing something here? Is this "security risk" online? Is Bill Gates going to surf through my internet toobz and rape me if I do this? :confused: Im scurred :(.

---

### Post by kerry_s on 2007-09-09
yes, it's online. lets say you hit a malicious site, that has a script that runs> sudo ./gotcha, gotcha being a script to copy over a program to say /etc/init.d and put it in the run levels.

and you have your settings
%admin ALL=ALL NOPASSWD:

you just got owned. hackers are sly it's like fishing, just put the line in the water and wait.

oh by the way, i've used a similar script on a friend to teach him a lesson. it would put a cron hourly job that put up a xmessage that just said "haha, i'm watching you" it drove him nuts. :)

---

