---
title: "calendar sharing"
date: 2007-02-04
forum: General Help
---

### Post by reckless2k2 on 2007-02-04
I'm looking to a way to do calendar sharing in Ubuntu. I only have use for a calendar sharing feature between my wife and I. We both use POP mail from comast that we pull down using Thunderbird on different computers but I'm looking for a way to share a calendar between the both of us. I've looked around a little and most require a mail server setup which I wouldn't have a use for. Could anyone point me to an open source calendar sharing solution with good setup documentation? I tired Hula but I seem to be having problems with apache2 because I can't dop the admin login to setup Hula. 

Thanks.

---

### Post by kanha on 2007-02-04
tried sunbird or not
i think that can help

---

### Post by reckless2k2 on 2007-02-04
The problem is that I need some kind of calendar server to share the calendars between users. I'm looking for something similar to calendar and contact sharing available in Outlook with Exchange but for Ubuntu using an open source calendar and contact application. I only need the calendar and contact sharing functions though. We both POP our mail down from Comcast.

---

### Post by wxlidar on 2007-03-27
> **reckless2k2 said:**
> The problem is that I need some kind of calendar server to share the calendars between users. I'm looking for something similar to calendar and contact sharing available in Outlook with Exchange but for Ubuntu using an open source calendar and contact application. I only need the calendar and contact sharing functions though. We both POP our mail down from Comcast.

Reckless2k2, any progress in setting up a calendar server? I'm looking for a similar solution.

-Dave

---

### Post by nocturn on 2007-03-27
You could try this: [http://rscds.sourceforge.net/](http://rscds.sourceforge.net/)

They have a debian repo.  It works quite well though most clients do not support CALDAV very well (that includes Evolution who refuses to support anything else!).

I'll blog about this in a couple of days BTW, its the final step in a quest I've been on for years now.

---

### Post by reckless2k2 on 2007-04-06
Sorry on the WAY late response but I ended up using Zimbra to fulfill my needs. It gave me more than what I wanted but helped me to consolidate everything into one app. Now I have a complete collab suite on one box serving my whole family. They can access anywhere through a web browser or use any client they like. My whole family uses the web client though because it's easier to have everything on the server especially if they are roaming. 

Zimbra is the way to go for collab/mail server needs and they have an Ubuntu package. It's super easy to install and maintain. There are a number of sites that list the few dependencies needed but all in all it's a simple install. You'll be up and running in about 15 minutes.

---

### Post by strabes on 2007-04-07
Sorry for the non-answer but why not use google calendar? You can share calendars with your friends etc.

---

### Post by reckless2k2 on 2007-04-08
I was looking for a solution that I had control of rather than using an outside solution. I guess I wanted the learning experience to be able to do it myself as well. I admit that Zimbra does 99% of the work for you I still have control of it and it resides in any manner I was on my LAN. The biggest issue was that my job blocks all outside "mail" sites and there was no way for me to ever access something like Google. With my own server, it is not blocked. Or at least yet. hahaha

---

