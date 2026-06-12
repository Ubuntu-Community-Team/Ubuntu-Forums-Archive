---
title: "Content Filtering Software"
date: 2007-07-24
forum: General Help
---

### Post by jodef on 2007-07-24
I have been searching for content filtering software for linux along the lines of Cybersitter for Windows. The main requirement would have to be that it is password protected and not even accessible by root user.

Googling and forum searches came up with combinations of iptables, squid proxy and dansguardian the only problem is that the sudo user would have access to password in conf files.

Any suggestions would be appreciated?

---

### Post by lisati on 2007-07-24
You might find that if you're using a router, it already has some kind of filtering capabilities built in. The router I use (one from Netgear) has an option to block sites based on keywords, and doesn't need any extra software. Router-based filtering has the advantage of being able to monitor ALL the computers connected to it, and works regardless of what kind of OS the computer might be running.

---

### Post by jodef on 2007-07-24
> You might find that if you're using a router, it already has some kind of filtering capabilities built in. The router I use (one from Netgear) has an option to block sites based on keywords, and doesn't need any extra software. Router-based filtering has the advantage of being able to monitor ALL the computers connected to it, and works regardless of what kind of OS the computer might be running.

Sorry should also mention that it must be a software solution. Thanks all the same.

---

### Post by Keen101 on 2007-07-24
I have a "quick-fix" solution, but it might not be exactly what you want.

The only content filtering I know for Linux, is through Firefox. using two neat Firefox plugins called WOT, and Foxfilter.

with foxfilter you can block access to the add-ons feature, so your kids cannot remove WOT or foxfilter.

plus foxfilter has a password for itself too. 

But, that can be read in a hidden file in the hidden firefox folder in your home directory. :( (hopefully your kids are not that smart)

I even wrote an article for Full circle magazine. It should be coming in one of the next issues. :D 

Like I said it is a "quick-fix" solution, and it can be bypassed by either finding the hidden file, or installing another browser. :(

hope this helps anyway,

-keen101

p.s. if you do want to try them out, and find that foxfilter say's "windows only" then don't hesitate to e-mail me, and I will help you. keen101 <at> gmail.com

---

### Post by mbeierl on 2007-07-24
Not sure I understand this - you want to lock the computer down so that even the administrator of the computer cannot undo it.  How do you ever maintain it then?

---

### Post by jodef on 2007-07-24
> **mbeierl said:**
> Not sure I understand this - you want to lock the computer down so that even the administrator of the computer cannot undo it.  How do you ever maintain it then?

The software is strictly to control internet surfing separate and apart from computer administration. I only want to have control over internet activity the user has full control otherwise.

---

### Post by swisscow on 2007-07-25
For a full web filtering system, easy to manage, have a look at the Christian Ubuntu website.

[HTML]http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html[/HTML]


Go to downloads, popular packages and then choose the web filtering for whichever version you are using. This is a script which will install a content filtering system.

This does some pretty major changes so read the instructions carefully and there is a thread on this forum somewhere. Basically it installs an easy to manage filtering system. I warn you though I tried this and I couldn't access the net at all with the filtering system switched on, but I'm using kubuntu which I'm told may make a difference.

---

