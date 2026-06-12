---
title: "Add command line to startup?"
date: 2018-01-14
forum: General Help
---

### Post by frappe792 on 2018-01-14
Hi all,

I would like to add the following command [COLOR=#111111][FONT=Consolas]pactl load-module module-bluetooth-discover [/FONT][/COLOR]to run on boot.

How can I make this happen - I have found so much conflicting data online specifically referring to adding the command line to /etc/rc.local - which I don't even have.

Can someone please advise if there was a straight forward way to do this??[COLOR=#111111][FONT=Consolas][/FONT][/COLOR]

---

### Post by Yellow Pasque on 2018-01-14
You can create /etc/rc.local, but it doesn't seem appropriate for what you're trying to do since it runs as root and may run before pulseaudio starts.

Is there a reason that using the "load-module module-bluetooth-discover" directive in /etc/pulse/default.pa doesn't work? You don't have it commented out, correct?

---

### Post by frappe792 on 2018-01-14
Thanks I checked the file and it isn't commented out.

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif


.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

---

