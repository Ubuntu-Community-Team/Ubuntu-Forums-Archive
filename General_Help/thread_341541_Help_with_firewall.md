---
title: "Help with firewall"
date: 2007-01-18
forum: General Help
---

### Post by skoalman88 on 2007-01-18
I recently installed Firestarter and I am constantly getting "hit detected" alerts (along with and IP addy. Should this concern me and if so, what can I do?


Thanks.

---

### Post by Stemp on 2007-01-19
Firestarter just warn you about «attacks». They are blocked, so it's not important ;)
But if you don't want to see those warnings just edit the file /etc/firestarter/configuration and change LOG_LEVEL=info to LOG_LEVEL=none
BTW you don't have to start firestarter (it's only a GUI), you are protected without running it

---

### Post by az on 2007-01-19
> **skoalman88 said:**
> I recently installed Firestarter and I am constantly getting "hit detected" alerts (along with and IP addy. Should this concern me and if so, what can I do?


Thanks.

Every computer on the internet gets this.  The only way to avoid it is to not be on the internet.

Just keep up-to-date with security updates and don't run any services that listen to the network unless you reallty need them.  Pick a strong password.

That's it.  A firewall on a desktop system does not afford you any more security.

---

### Post by skoalman88 on 2007-01-19
Thanks.

---

