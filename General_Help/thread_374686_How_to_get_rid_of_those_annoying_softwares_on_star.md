---
title: "How to get rid of those annoying softwares on startup?"
date: 2007-03-02
forum: General Help
---

### Post by rodrigo666 on 2007-03-02
Greetings,

Every time I start my Ubuntu Box, there's a lot of software that is loaded with it.

I tried to remove some of they (like beagle and compiz - I don't use compiz anymore, I use Beryl) from the System>Preferences>Sessions>Startup Programs, but they still get loading on the start of the session (by the way, compiz and beagle can't be removed from the place above mentioned because there aren't the option for that).

For a example, another software that insists to load on every boot is Gdesklets, but I already removed that from the "Startup Programs" on Sessions.

What should I do?

- Evolution is another pain in the $%*# -

---

### Post by zapcojake on 2007-03-02
research sysv-rc-conf in the forums, it will show you all kinds of stuff

---

### Post by rodrigo666 on 2007-03-05
Nope, that didn`t worked. The command suggested only shows softwares that start by default and runs in the background.

I`m trying to disable and remove from startup some softwares that I have to close on every start, namely: Gdesklets, Compiz, Evolution etc.

---

### Post by kellsens on 2007-03-05
Hi Rodrigo !

   Try using BUM (Boot-Up Manager). Maybe will help you.

    sudo apt-get install bum

Kellsens

---

### Post by rodrigo666 on 2007-03-05
Thanks, but all of your help is related to disable services of the system that load in the startup.

That's not what I need. I need to solve a problem of softwares (programs) that runs on every startup, namely: Gdesklets, Compiz, Beagled etc.

---

