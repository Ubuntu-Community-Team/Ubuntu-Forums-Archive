---
title: "[SOLVED] Remove apache to start on startup"
date: 2008-04-15
forum: General Help
---

### Post by tommyhakinen on 2008-04-15
Hi,

I am using Ubuntu Gutsy desktop and have LAMP installed. Apache always run on startup as when I enter "http://localhost/", the content of my webroot directory appear. I have tried to look at the startup programs but could not find apache.

I also tried this code :
> 
update-rc.d foo default # adds a service to the default runlevel
update-rc.d foo remove # removesd a service from the default runlevel


but it seems not working.
is there anything i can do to fix this?

thank you.

Regards,

tommy

---

### Post by Ben Miller-Jacobson on 2008-04-16
Did you literally enter that exact code? If so, no wonder it didn't work. "foo" is a metasyntactic variable; you are meant to replace "foo" in that code with something to be determined based on the desired effects. In this case it would be something apache related and if you were lucky it could be as simple as just "apache", though I don't know if that is the case.

There is also an easy graphical method: click on system, then administration, then services. The apache web server should be at the bottom of the list.

Good luck

--Ben Miller-Jacobson

---

### Post by rahearn on 2008-04-16
In System->Administration->Services there should be a checkbox for apache2, or it might say "Web Server" or something like that (I don't have apache installed right now).  Make sure that box is unchecked.

If for some reason that entry does not exist, I've had better luck using the program sysv-rc-conf to turn on and off services.  Once it's installed run:

sudo sysv-rc-conf

and uncheck any boxes on the apache2 line to make it so apache2 does not run automatically ever.

---

### Post by tommyhakinen on 2008-04-16
> 
In System->Administration->Services there should be a checkbox for apache2, or it might say "Web Server" or something like that (I don't have apache installed right now). Make sure that box is unchecked.


WOW...It works after I restarted.Thanks.

---

