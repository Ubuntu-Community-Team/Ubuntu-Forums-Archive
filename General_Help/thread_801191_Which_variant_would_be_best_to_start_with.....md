---
title: "Which variant would be best to start with...."
date: 2008-05-20
forum: General Help
---

### Post by three_jeeps on 2008-05-20
Hi:

I want to install a version of Ubuntu but not sure what variant would offer the most amount of what I need ‘built in’…but also offer the 'least path of resistance' in support the following things:

- Will be a guest OS under VMware
- Can install and run the latest release of Apache
- Can install and run some net services (FTP, telnet, etc)
- Can install and run mail server (preferable sendmail) for local machines in LAN, behind a router, and expand to being a real server outside of LAN.
- Can install and run HylaFAX FAX server which can send received faxes to machines on the LAN as well as web, and can receive docs from LAN and web clients to send as a fax
- Can install and run some x10/home automation pkgs/programs, such as: Pluto, HomeDaemon ([http://www.denninger.net/homedaemon.htm](http://www.denninger.net/homedaemon.htm)),  and run CM11a daemon ([http://www.danlan.com/homeauto.html](http://www.danlan.com/homeauto.html))
- install and run a C/C++ development environment (e.g. GNU C)
- Run various scripting languages: Python, perl, tkl, javascrip
- some basic user functionality would be desirable (window based UI, open office, run mySQL, web browser, etc)

Can be somewhat easily ‘cut down/configured’ to run the minimal # of processes to support the above

And the reason for the small runtime footprint is that ultimately the target hw is a 1 GHz-1.5 GHz laptop or mini-itx board with a Celeron processor.

Most of the apps listed above have a version targeted to Debian, which hopefully I can apt-get to install/run, or compile with minor mods to run on the target platform(s).  

I am concerned that maybe one of the Ubuntu flavors might be a little overly constrained (e.g. the server version) that would limit the flexibility and potential growth for future dabblings (e.g. serial line and usb interfaces) but has compactness/efficiency of a smaller footprint…otoh, a version that would not be as compact but is configurable/extensible and would not limit my application/development options would be more desireable (hmmm workstation?)

You thoughts and suggestions on this is appreciated…..
Thanks
-J

---

### Post by Het Irv on 2008-05-20
With target Hardware like that I am inclined to suggest Xubuntu, but if you haven't used Linux before it is slightly harder to use than the other Ubuntu flavors.  I haven't used Xubuntu extensivly so I am not sure what it can/cannot do, but I am sure If you have any problems, a post or two here in the forums should help you out.

---

### Post by three_jeeps on 2008-05-20
> **Het Irv said:**
> With target Hardware like that I am inclined to suggest Xubuntu, but if you haven't used Linux before it is slightly harder to use than the other Ubuntu flavors.  I haven't used Xubuntu extensivly so I am not sure what it can/cannot do, but I am sure If you have any problems, a post or two here in the forums should help you out.

thank you!..I forgot to mention that I cut my UNIX teeth on Berkeley V6 and V7 doing driver design, am a Slackware hacker from way back, and have moved through RH 2-9, FC 1-4, and as of late, Debian (woody, sarge, and etch...) Am comfortable doing kernel reconfigs/recompiles, installing/configuring programs, C development, and admin tasks such as setting up apache, sendmail, etc.  So I sorta know my way around 'linux' enough to be dangerous....what tends to be a time sink with me is trying to find out where all the stuff is stored in different versions/distros, and finding out the hard way that some features that I thought were 'standard' now are not...

---

### Post by Het Irv on 2008-05-20
It sounded like you knew your way around, but I wanted to be sure.  The other suggestion would be fluxbuntu, but have never used that, so I have no idea what that is like.

---

### Post by three_jeeps on 2008-05-21
> **Het Irv said:**
> It sounded like you knew your way around, but I wanted to be sure.  The other suggestion would be fluxbuntu, but have never used that, so I have no idea what that is like.

Hmmm, I looked all over the Ubuntu site and can't find 'fluxbuntu'.....what is it?/where is it?
Thanks
-J

---

### Post by Het Irv on 2008-05-21
[http://fluxbuntu.org/](http://fluxbuntu.org/)

There isn't much on that site, but it is a Ubuntu Derivative using the Fluxbox Window Manager.

---

