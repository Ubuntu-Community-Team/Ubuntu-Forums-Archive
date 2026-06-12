---
title: "SABnzbdStatus FF Plugin No Workie in Ubuntu?"
date: 2007-11-29
forum: General Help
---

### Post by trmentry on 2007-11-29
I just found this great FF plugin for SABnzbd.

[https://nzbdstatus.bountysource.com/](https://nzbdstatus.bountysource.com/)

Its a plugin very similar to the Greasemonkey script 'SABnzbdIcon'.  But this plugin doesn't need Greasemonkey to function.

I got it working on my vmware windows machine while I was at work and it works very nicely.  I got home and installed it into FF 2.0.0.10 on Gutsy and it doesn't work.  

It shows the SAB icon to click on but nothing gets queued.  However I have it config'ed the same way as the windows setup.


I've double checked all my settings and I'm at a loss.  

Running: sabnzbd 0.2.7 (i guess this is sabnzbd+ as the original author stopped at 0.2.5) with the NOVA 0.4.4 templates.

has anyone else had this issue?  

Thanks

---

### Post by duz on 2007-12-01
Author of the extension here.  I know it runs fine in Ubuntu because that's what I use.  Can you run Firefox from a virtual terminal and see if any errors announce themselves?

---

### Post by trmentry on 2007-12-01
> **duz said:**
> Author of the extension here.  I know it runs fine in Ubuntu because that's what I use.  Can you run Firefox from a virtual terminal and see if any errors announce themselves?

Thank you for the reply.  I opened a report on your dev site as well.  Sorry for the duplication, but wasn't sure if you lurked here. :)

Anyway... I would love too... but I'm not familuar with the virtual terminal for firefox.  Can you (or anyone) point me in the right direction?


thank you.

---

### Post by duz on 2007-12-01
I don't lurk here much, I mainly keep an eye on my logs ;)
And not a terminal in Firefox, the regular terminal under Accessories.  Run Firefox from there after closing all other instances of Firefox.  The command is `firefox` in case you weren't sure.  I have the extension dumping errors there for ease of debugging.

---

### Post by trmentry on 2007-12-01
> **duz said:**
> I don't lurk here much, I mainly keep an eye on my logs ;)
And not a terminal in Firefox, the regular terminal under Accessories.  Run Firefox from there after closing all other instances of Firefox.  The command is `firefox` in case you weren't sure.  I have the extension dumping errors there for ease of debugging.


OK... dropped to a console and typed firefox.  Which launched... went to v3 and selected a post.  Clicked on the icon and nada.

And nada on console as well.

The only thing I can think of is sabnzbd isn't on this machine.. its on my server... so its not [http://localhost:8080/sabnzbd](http://localhost:8080/sabnzbd)

but [http://hoth:8000/sabnzbd/](http://hoth:8000/sabnzbd/)    (yes... hoth is in DNS and resolves just by the name and not fqdn)

Which works on the XP install.  

I stopped and restarted sab to be sure... nothing changes. :(

---

### Post by duz on 2007-12-01
Ok, so it's not erroring out somewhere.  I've a few guesses.  I'm cleaning up the AJAX code at present, that might fix it.

---

### Post by trmentry on 2007-12-01
> **duz said:**
> Ok, so it's not erroring out somewhere.  I've a few guesses.  I'm cleaning up the AJAX code at present, that might fix it.

Ok... Thank you.  If you would like to have me test things please let me know.

---

