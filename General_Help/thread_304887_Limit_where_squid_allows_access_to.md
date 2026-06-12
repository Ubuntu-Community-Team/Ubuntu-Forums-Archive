---
title: "Limit where squid allows access to"
date: 2006-11-22
forum: General Help
---

### Post by RichJacot on 2006-11-22
Hello,

Is there a way to limit where squid allows users to go?

I need to configure squid to be fairly locked down.  I have figured out how to limit what IPs can access squid, but I can't figure out how to limit what url's are allowed.  (i.e. I only want people to be able to get to [www.yahoo.com](www.yahoo.com), [www.sun.com](www.sun.com), ubuntuforums.org and [www.google.com](www.google.com))

Does anyone have any experience with this or ideas?  I've been google'ing on it for awhile now with no success.  Everything I try blocks everything or nothing.](*,) 

Thanks,
Rich

---

### Post by speedman on 2006-11-22
apt-get install dansguardian

[http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=dansguardian+howto](http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=dansguardian+howto)


Regards,

SM

---

### Post by RichJacot on 2006-11-22
Anything a little less complicated (for the lack of a better term)?

This is going to be a 24/7 production server and I'd prefer to just make modification to the squid.conf file and not install another application to accomplish blocking all but allowed URLs.  Less to go wrong for a 99.995% uptime environment (and yes, I'll have two of these servers behind a VIP).

Thank you for the suggestion though.  I will keep it in mind in case what I'm wanting to do is not possible without using DansGuardian.

Rich

---

### Post by speedman on 2006-11-22
DG runs for us in numerous client installs 24/7 without a problem - it's more stable than squid is.


Regards,

SM

---

### Post by NetworkGuy on 2006-11-22
DG needs a proxy server in front of it.   All DG does is content filter.

In Squid you can set an ACL allow to only allow certain people to access a list of sites,  however if you want multiple people to have different access control lists, then you need to set up authentication.

---

### Post by speedman on 2006-11-22
Of course DG needs squid - I didn't say otherwise.  However, stability wise DG is more solid that squid under heavy load (500+ user LANS).  I was merely replying to the OPs concern about availability.


Regards,

SM

---

### Post by echo $USER on 2006-11-22
I use tinyproxy for content filtering and proxy service... breeze to set up...

[http://ubuntuforums.org/showthread.php?t=122011&highlight=tinyproxy](http://ubuntuforums.org/showthread.php?t=122011&highlight=tinyproxy)

---

### Post by SergioLopes on 2008-05-15
Sorry for opening this old thread, but i have a similar problem... 
I have my ubuntu running squid + dg, with squid authentication, but i need to create a user limited to just a list of pre-configured sites... 

It's too hard ? 
Anny suggestions ? 

Thanks in advance.
Best regards

SergioLopes
Portugal

---

