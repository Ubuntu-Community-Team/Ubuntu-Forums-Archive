---
title: "Tor and Vidalia"
date: 2007-09-01
forum: General Help
---

### Post by intense.ego on 2007-09-01
I have managed to install vidalia, but am confronted with a problem. When I open the application and click on "Start Tor," an error message pops up. It says:

Warning - connection_create_listener(): Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Warning - Failed to parse/validate config: Failed to bind one of the listener ports.
Error - tor_init():Reading config failed--see warnings above. For usage, try-h.


Does anyone know what I should do?

---

### Post by Seisen on 2007-09-01
What happens when you put 

```
sudo /etc/init.d/tor stop
``` in the terminal.

---

### Post by intense.ego on 2007-09-01
Thanks a lot. I turned Tor off, then just turned Vidalia on and that was that.

---

### Post by Bobba on 2008-02-22
This fix didn't work for me as I get the following message

$ sudo /etc/init.d/tor stop
Stopping tor daemon: not running (there is no /var/run/tor/tor.pid).

However this worked:
sudo killall tor
and then you can run vidalia

---

