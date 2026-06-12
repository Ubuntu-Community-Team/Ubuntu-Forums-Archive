---
title: "Using synaptic for automatic upgrades"
date: 2007-08-06
forum: General Help
---

### Post by holst on 2007-08-06
Hi!

I would like to use Synaptic to keep my computer updated even when I am not sitting at the keyboard. It should download by itself and install all packages which does not require "hands on" support. If any side effects like "reboot" is detected the computer should reboot.

Is this doable? It must be doable without logging into the computer on the console. 

If this is not doable via Synaptic, do you know of a way to do it with Aptitude or Apt-tools?

Thanks for your help!

Regards,
Henrik Holst, Sweden

---

### Post by dpar on 2007-08-07
I doubt it, but if it was, it would be very insecure because you have to have root priveleges to install stuff. You would be logged in as root all the time to do this.

---

### Post by az on 2007-08-07
Applications  - Add-remove - Preferences - Updates - in Automatic Updates, tick Install security updates without confirmation.  You will only get security upgrades and your box will not reboot on it's own...

---

