---
title: "Host app over web?"
date: 2018-07-11
forum: General Help
---

### Post by warmango on 2018-07-11
So what im trying to do is something like what RollApp has done, only issue is that they claim its "Unable to be replicated" which i find is utter bullcrap. this is the transcript of their reply when i asked how it works, And YES, they do use a ubuntu system for the apps

> [FONT=Arial]We host the applications in the cloud using the platform we developed. It indeed uses Ubuntu as the underlying OS to run the applications, but it cannot be replicated using the Ubuntu itself.
 For what you need you may want to look into VNC and related components.[/FONT]

And i have spent a little over a year trying to figure this crap out, and i have no luck, so im turning to the forums here where people are serious and the discussion wont spiral into off topic chaos.

Any ideas?

---

### Post by warmango on 2018-07-12
Bump?

---

### Post by Holger_Gehrke on 2018-07-12
This used to be almost trivial back in the day when Java in the browser was still usable. Set up a vnc-server, configure it to serve up a webpage with a vnc-client-applet, done. Nowadays you wouldn't do that, not only because Java in the browser is no longer an option, but also for security reasons since vnc is not encrypted (there is an encrypted variant of the protocol using ssl, but AFAIK that's never become standard).

I imagine they've basically written something like a vnc client in JS using https as transport and have VMs with proprietary vnc-like servers.

Holger

---

### Post by warmango on 2018-07-13
Well... great.

On the topic of VNC, i am trying to get it to autostart on uby18, dont care how, just aslong as its quick, painless, and doesnt require me to SSH and manually start it, like an autostart script

---

