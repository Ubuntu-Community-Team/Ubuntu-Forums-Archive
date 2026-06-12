---
title: "Cannot uninstall default apps"
date: 2007-02-14
forum: General Help
---

### Post by Centipeed on 2007-02-14
So, I've got Ubuntu installed on my laptop, and there are some programs that come with it that I'd rather not have in there, because they're just taking up space and I don't ever and won't ever use them (Stuff like Evolution mail client, Floppy formatter etc).

Whenever I try and uncheck them in Add/Remove Applications so that I can click Apply and it can uninstall them, I get this error:

[I]{Application name} cannot be installed on your computer type (i386)
Either the application requires special hardware features or the vendor decided to not support your computer type.[/I]

Besides the fact that it acts as if I'm installing stuff, when it's the opposite (These apps are already installed), it happens for every application I try and uncheck.

Anyone know about this?

---

### Post by john.nicholls on 2007-02-14
Have you tried using Synaptic?

---

### Post by Centipeed on 2007-02-15
It's fine now. In the end, I just removed them from the applications menu. All I really wanted was to get rid of the shortcuts there that I would never use and were just cluttering it up. Besides, some of this stuff needs the Desktop package to be removed as well :S

---

### Post by christoforever on 2007-02-15
you could always try:

sudo aptitude remove package-name

this usually works for me.

---

### Post by fragos on 2007-02-15
Removing the desktop package isn't harmful since it is only a shortcut to install a lot of other things.  None of these are removed when the desktop package is.

---

