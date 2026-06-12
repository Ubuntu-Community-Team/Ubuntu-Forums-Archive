---
title: "Davmail only works in Sudo"
date: 2014-12-30
forum: General Help
---

### Post by justinalf2 on 2014-12-30
Wow, I haven't posted on these forums in years!  Usually Ubuntu just works, but I'm having a terrible problem.  

I'm on Kubuntu 14.10 usuing Davmail and Thunderbird to connect to my exchange email.  I setup according to this thread : [http://nknu.net/ubuntu-14-04-exchange-configuration-thunderbird-pidgin/](http://nknu.net/ubuntu-14-04-exchange-configuration-thunderbird-pidgin/) 
and everything works great.  The only problem is, I have to run davmail in sudo under terminal in order for it to work.  Otherwise, I get a java.net connectionexeption Connection refused.

Anyone know how I can bypass this error from Davmail, or perhaps give it sudo permissions?  I need this email to be flawless for work.

---

### Post by JKyleOKC on 2014-12-31
Since I don't use the KDE desktop and its configuration files differ, I can't give you specific help, but perhaps I can provide a hint that can put you on the right track. Most things that communicate with the outside world, such as e-mail, use ports that by default are restricted to only the superuser/root. However they usually have specific "group" attributes that provide members of that group the ability to masquerade as necessary to use the needed ports. This is part of the general security approach common to Linux.

In my systems there's a "Users and Groups" utility available through a "System" category on the main menu, that includes checkboxes permitting a user to perform certain actions. These boxes add the user to the group defined for that action. I would expect KDE to have something similar, and telling the system to let you use e-mail should take care of the problem.

Let us know if this helps -- good luck!

---

