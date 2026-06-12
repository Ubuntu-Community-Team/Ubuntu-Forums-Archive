---
title: "Module problems and uname misinformation"
date: 2004-11-07
forum: General Help
---

### Post by stevho on 2004-11-07
When I boot and shutdown I get multiple error messages like:
"Can't open dependencies file /lib/modules/2.2.20-idepci/modules.dep (No such file...)"

When I try to modprobe I get the same message.

The first line in dmesg begins "Linux version 2.2.20-idepci..."
and before this line in /var/log/messages I have:-
"Cannot find map file
  No module symbols loaded"

'uname -a' reports  "Linux ... 2.2.20-idepci ... i686".

lsmod shows no modules loaded, even though /etc/modules lists 6 modules.

The only directory I have in /lib/modules/ is '2.6.8.1-3-386'.  
Why does my system seem to be expecting modules to be in '2.2.20-idepci'?
How do I point it in the right direction?

Also where does uname get its info from?

Thanks.

---

### Post by p!=f on 2004-11-07
There's no linux kernel 2.2.20 in **Ubuntu** but in **Debian Woody** repositories.
Did you install it from **Woody's** sources?

If a purpose of that machine is not a server with some unique setup, I don't see a point why to run 2.2.20 kernel nowadays. What's more, 2.2.20 is six releases behind the "fresh" 2.2 line (2.2.26). :)

Be as be, boot to the default 2.6.8.1 kernel.

Edit: Typos...

---

### Post by stevho on 2004-11-07
[QUOTE=p!=f]There's no linux kernel 2.2.20 in **Ubuntu** but in **Debian Woody** repositories.
Did you install it from **Woody's** sources?[/QUOTE]

I installed from a CD, not an official Ubuntu one (I ordered one a week ago but I'm still waiting for it). This was from a distributer.

I know Ubuntu uses 2.6, and I know I have 2.6.8.1 (eg: from synaptic and the presence of /etc/modules/2.6.8.1...) but the module loader and uname both believe I have 2.2.20!

The question is where do they get their information from and how can I put them right?

---

