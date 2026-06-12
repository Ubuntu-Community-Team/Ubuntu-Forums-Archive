---
title: "Ubuntu - Of Clients and Servers"
date: 2008-01-17
forum: General Help
---

### Post by MaloKorrigan on 2008-01-17
I'm new the the Linux scene and I'm hoping to do some radical stuff at work, so just a bit of back story before beginning my dilemma. (If this has been posted in the wrong area, please move the thread to the correct area, thanks)

We have at work a Windows 2003 SE server with Windows XP Pro clients connected.

Users log in by entering their user name and password assigned to them using the Active Directory on the server.

User profiles are preset and when a user logs in, the profile is downloaded and Group Policies on the server prevent users from wandering about changing things.


This is my question, is it possible to replicate what we have in our Windows environment (stated above) using Ubuntu? possible walkthroughs, howto's or even a point in the right direction to what the equivalent software is called (for example, what program emulates Active Directory in the Ubuntu environment?)

Thanks in advance, hopefully I'm not been too much of a pain!

---

### Post by mmichalik on 2008-01-17
This is a tough question that has a lot of debate going on but, the quick answer is yes.  OpenLDAP on a Ubuntu server should do everything you will need it to.

Perhaps others can post more informative responses?

---

### Post by MaloKorrigan on 2008-01-18
Many thanks for pointing me in some direction, I didn't even know where to start before I posted this thread.

Been reading up on OpenLDAP and it seems like an open source version of Active Directory.

Will try and get it running to see if I can a client to link to a server.

Any further help will much appreciated thanks!

---

