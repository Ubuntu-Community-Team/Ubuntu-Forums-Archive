---
title: "disable printer discovering in 16.04"
date: 2016-07-14
forum: General Help
---

### Post by gianluca3 on 2016-07-14
hello,

my ubuntu 16.04 continuously discovers the network printers (i'm in a department they are a lot...).

i tried  by disabling the corresponding option under the "view" menu by running:

```
sudo system-config-printer

```
any help?

thanks
g.

---

### Post by GU4$+7rxH#@ on 2016-07-15
Hello

I found a possible topic for this present problem

[URL="http://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation"]http://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation

[http://brainextender.blogspot.com/2009/05/disable-cups-automatic-remote-printer.html](http://brainextender.blogspot.com/2009/05/disable-cups-automatic-remote-printer.html)
[/URL]I hope it works.[URL="http://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation"]
[/URL]

---

### Post by gianluca3 on 2016-07-18
thank you

it only worked with the last post, i.e.:

> sudo nano /etc/cups/cups-browsed.conf

and changing

> BrowseRemoteProtocols dnssd cups 

to 

> BrowseRemoteProtocols none



best
g.

---

### Post by jones-home on 2017-05-10
Thanks, I have three wifi network computers that have kept on being 'rediscovered' and set to poor drivers (that don't support colour or duplexing) every time I switch on my computer. 
So far this is the only mend that has worked out of many community suggestions I have tried.

The big question is WHY DOES GNOME HAVE THIS TERRIBLE AND INCONVENIENT SO-CALLED 'FEATURE'?
Who is it that thinks it is somehow a convenience? It should be deleted, or if someone does have a reasonable argument for it that I cannot think of, IT SHOULD BE EASY TO SWITCH OFF IN SETTINGS.

---

### Post by luca-dgh on 2017-09-02
I thank a lot for your answers, they helped me too to fix that issue. I applied the solution posted by **gianluca3** in post #3.
However I found that curiously Firefox still shows a generic "laserjet printer" that is "refusing jobs", apart from the correct printers. No others programs are still showing that generic printer (libreoffice,pdf reader, editors, chromium, etc.).

That's very strange: Firefox has a private net printers discoverer?

---

### Post by pascal-ggl on 2017-12-04
> **luca-dgh said:**
> I thank a lot for your answers, they helped me too to fix that issue. I applied the solution posted by **gianluca3** in post #3.
However I found that curiously Firefox still shows a generic "laserjet printer" that is "refusing jobs", apart from the correct printers. No others programs are still showing that generic printer (libreoffice,pdf reader, editors, chromium, etc.).

That's very strange: Firefox has a private net printers discoverer?

I experienced the same problem (currently using 17.10) and solved it by editing /etc/avahi/avahi-daemon.conf and changing the these lines to "no":

    use-ipv4=no
    use-ipv6=no

Now I really only have the printers that I installed.

---

