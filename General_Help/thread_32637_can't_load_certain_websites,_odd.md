---
title: "can't load certain websites, odd"
date: 2005-05-08
forum: General Help
---

### Post by khu19 on 2005-05-08
Hi I've been using Ubuntu since Hoary came out and love it.  I'm experiencing a strange problem loading websites in Firefox 1.0.2.

I can browse the web perfectly fine except I can't load certain websites.  The biggest is [www.bensbargains.net](www.bensbargains.net)

I know it works because I've tested it on my windows bootup.  I also installed Opera8 in Ubuntu to test if it was firefox but still nothing.

Why would my computer have problems connecting to certain websites?  Thanks.

Keep up the great work.


Thank you,
Kevin

---

### Post by Xian on 2005-05-08
[QUOTE=khu19]I can browse the web perfectly fine except I can't load certain websites.  The biggest is [www.bensbargains.net](www.bensbargains.net)[/QUOTE]
Do you mean the page won't load at all or that is has an improper look?

---

### Post by khu19 on 2005-05-08
[QUOTE=Xian]Do you mean the page won't load at all or that is has an improper look?[/QUOTE]

It just won't load at all. It's as if the website is offline when it isn't.

---

### Post by Xian on 2005-05-08
Do you have a firewall on your box or any domains added to your hosts file?

---

### Post by khu19 on 2005-05-08
[QUOTE=Xian]Do you have a firewall on your box or any domains added to your hosts file?[/QUOTE]
I tried connecting to the site with and without the firewall but no changes.  How do I check if domains are in my hosts file?

---

### Post by khu19 on 2005-05-08
This is what my /etc/host.conf has:

```

order hosts,bind
multi on

```

I can ping the url perfectly fine, but just wont render in any web browser.

---

### Post by Xian on 2005-05-08
[QUOTE=khu19]I tried connecting to the site with and without the firewall but no changes.  How do I check if domains are in my hosts file?[/QUOTE]
If you didn't add them then there shouldn't be any additional entries.
It's located in /etc/hosts. I'd imagine you just have the default settings.

---

### Post by Xian on 2005-05-08
Thy clicking on [THIS](http://bensbargains.net/email.shtml) link.
It's on the same domain but a different page. Any difference?

---

### Post by khu19 on 2005-05-08
[QUOTE=Xian]Thy clicking on [THIS](http://bensbargains.net/email.shtml) link.
It's on the same domain but a different page. Any difference?[/QUOTE]
Nope same thing.  Basically keeps timing out...I'm so confused.

---

### Post by Xian on 2005-05-08
Try to load the page again in Opera and when it hangs(?) hit the F5 key.
That will force reload the site and maybe get things moving.

Otherwise I'd say it's a local issue with firewall, ISP, etc.

---

### Post by khu19 on 2005-05-08
[QUOTE=Xian]Try to load the page again in Opera and when it hangs(?) hit the F5 key.
That will force reload the site and maybe get things moving.

Otherwise I'd say it's a local issue with firewall, ISP, etc.[/QUOTE]
Nothing.  Anything else?  Thanks for trying so far, I appreciate it man.  

If it's local then it's only for this Ubuntu install, because when I'm dual booting nix and windows and the windows boot can load perfectly fine.  Can't see why this would occur though...

---

### Post by Xian on 2005-05-08
I don't guess you happen to have a LiveCD laying around somewhere? It would be interesting to load that and see if you can duplicate this in another Linux session. But if not I would just wait it out a bit and see if it's just a temporary issue, since really I can see no legitimate reason for such an occurrence.

---

### Post by khu19 on 2005-05-08
I found the root of the problem.  It appears that Firestarter (my firewall) was not properly shutting down.  Even when I closed the application the process would still run, unnoticed.  Odd, but the problem is fixed.

Thanks Xian for the help!


see you around the forums

---

