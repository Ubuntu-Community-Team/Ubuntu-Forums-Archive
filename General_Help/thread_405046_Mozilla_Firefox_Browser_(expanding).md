---
title: "Mozilla Firefox Browser (expanding)"
date: 2007-04-09
forum: General Help
---

### Post by Kizilbas on 2007-04-09
How can I expand the Firefox browser so it takes the upper screen (The strip where 'Applications' & system time/date is displayed).

I want to hide the top part of the screen so the firefox browser can take more space.

Sorry I'm very newb on linux systems.

---

### Post by chewearn on 2007-04-09
1) You can auto-hide the top panel; right-click on the panel > Properties > select Autohide

2) Toggle Firefox to fullscreen by pressing F11 (while Firefox has the focus).

---

### Post by chewearn on 2007-04-09
3) You can enable hide button on the top panel; right-click on the panel > Properties > select "Show hide buttons".  Then, when you click on the hide button, the panel will slide off-screen.

---

### Post by Kizilbas on 2007-04-09
Thank you AstalaVista, that really helped.
I guess I would have found my way to those if I looked 'into' the system with a determining eye, but I have lots of jobs to do and they just don't end to give me some free time :).

If you wouldn't mind I would Iike to ask you another question, which I guess you probably would be familar with;

Do I need an antivirus software & firewall for the linux I'm using now (Xubuntu).
My router is a Netgear and it has its own firewall if I'm not mistaken.

If I do need an antivirus or and a firewall, what are the ones you personally recommend AstalaVista?

/Thanks for the help :)

---

### Post by Kizilbas on 2007-04-09
I have another question, I am using Xubuntu 6.06 Dapper (I think its Dapper)
Do you think I should update it?

---

### Post by chewearn on 2007-04-09
> **Kizilbas said:**
> Thank you AstalaVista, that really helped.
I guess I would have found my way to those if I looked 'into' the system with a determining eye, but I have lots of jobs to do and they just don't end to give me some free time :).
No problem, glad to help.:)

> Do I need an antivirus software & firewall for the linux I'm using now (Xubuntu).
My router is a Netgear and it has its own firewall if I'm not mistaken.Ubuntu by default has all unused ports in stealth.  This is equivalent to running Windows with a good software firewall.  As for antivirus, I'm not aware of any which infects linux (though I should say I'm not a network security expert, just a user).  Normally, people who runs anitvirus in ubuntu are dual booting to Windows.  The antivirus allows them to catch Windows viruses in data files or emails for example.
Hardware routers (netgear, linksys etc)  functions as rudimentary firewall by providing NAT function and steathing unused ports.  A good place I always visit to catch up on network security is grc.com  There, you can also find the ShieldsUp page where you can test your network exposure to the internet.

> If I do need an antivirus or and a firewall, what are the ones you personally recommend AstalaVista?I don't use any antivirus or firewall in my ubuntu system, so I don't have any personal recommendation there.  On my network, I used a linksys router, which should be similar (function wise) to your netgear router.  On a Windows machine, I have Sygate firewalll and and Avast! antivirus.

---

### Post by chewearn on 2007-04-09
> **Kizilbas said:**
> I have another question, I am using Xubuntu 6.06 Dapper (I think its Dapper)
Do you think I should update it?
If you mean update to 6.10, then it depends on your personal situation.  6.06 LTS means it will continue to be supported for a long time (means you don't have to upgrade if you don't want to = stability).  Version 6.10 is supported for 2 years (I think) so you have to continuously upgrade at least every 2 years.  But certain software in 6.10 are newer version (e.g. Firefox 2 instead of 1.5).  Though, it is possible to install Firefox 2 in 6.06 (see aysiu website: psychocats.net).
Personally, as home user, I feel it is better to upgrade, to take advantage of the  improvements in newer versions (including newer kernel).  I'm looking forward to Feisty official release because it comes with better wireless support.

---

### Post by Kizilbas on 2007-04-09
Thank you AstalaVista.

I had a copy of Windows XP Professional but I deleted it because I no longer use it.
+ Thanks for all the links and information

/Are you a member of AstalaVista or in anyway an Administrator there?
Just curious..

---

### Post by chewearn on 2007-04-09
Not an administrator, just ordinary member.  Also, no relationship to astalavista.com :)

---

### Post by Kizilbas on 2007-04-09
okay :)

---

### Post by noynac on 2007-04-09
> **AstalaVista said:**
> ...2) Toggle Firefox to fullscreen by pressing F11 (while Firefox has the focus).

You may also want to look at the FullerScreen extension at:

[http://tinyurl.com/yv8rop](http://tinyurl.com/yv8rop)

---

### Post by Kizilbas on 2007-04-09
> **noynac said:**
> You may also want to look at the FullerScreen extension at:

[http://tinyurl.com/yv8rop](http://tinyurl.com/yv8rop)

thanks :)

---

### Post by nanog on 2007-04-09
Having ports *stealthed* is in no way similar to having ports **blocked**. I have had my *stealthed* ports hacked on an updated Ubuntu server. 
I recommend Firestarter as an easy to configure firewall. I also recommend ClamAV for Ubuntu virus scan. (Both are available as supported Ubuntu repos.)

---

### Post by Kizilbas on 2007-04-09
> **nanog said:**
> Having ports *stealthed* is in no way similar to having ports **blocked**. I have had my *stealthed* ports hacked on an updated Ubuntu server. 
I recommend Firestarter as an easy to configure firewall. I also recommend ClamAV for Ubuntu virus scan. (Both are available as supported Ubuntu repos.)

Yes nanog having ports blocked or stealthed doesn't stop an attacker from attacking or gaining control, they simply then exploit your system.

Thank you very much for your recommendation :)

---

