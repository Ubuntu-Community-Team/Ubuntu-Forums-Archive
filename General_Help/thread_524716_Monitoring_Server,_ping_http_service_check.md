---
title: "Monitoring Server, ping? http service check?"
date: 2007-08-13
forum: General Help
---

### Post by phillips321 on 2007-08-13
Hi guys,

I would like to monitor to see if my server is up.

The first option would be just to ping the server every minute and alarm if there isn't a response.

What would be best though would be to check for a http service and if it responds.

How would this be done?

I guess i need to write a script and then add this to cron.

Any idea how this script would go?

Cheers guys

P.s. Preferably an audible and visual alarm would be great

---

### Post by kidders on 2007-08-14
Hi there,

I guess you could use telnet to try to open a connection to your web server. Audio warnings are straightforward, but you'd probably be relying on somebody being logged into a graphical environment to provide a visual message. You could use "w" or "who" to check that though.

---

