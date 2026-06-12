---
title: "synaptic error after power outage .."
date: 2007-08-08
forum: General Help
---

### Post by qarews on 2007-08-08
my computer got restarted due to a power outage, while synaptic was opened but **not** working [installing deleting or else]


now i have this error while trying to update [i got an update notification]

[B][FONT="Lucida Console"]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/extended_states (1)'[/FONT][/B]


and this error in synaptic

[B][FONT="Lucida Console"]E: Unable to parse package file /var/lib/apt/extended_states (1)
E: _cache->open() failed, please report.[/FONT][/B]


and this one on apt-get

[B][FONT="Lucida Console"]
@ : ~ $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Error!
E: Unable to parse package file /var/lib/apt/extended_states (1)[/FONT][/B]

so .. i need some help

thank you in advance

---

### Post by ThrobbingBrain66 on 2007-08-08
Just try renaming the file to extended_states_tmp

Then apt-get, Synaptic and Update Manager should all work.
If so, that file can safely be removed or leave it as renamed just in case, thought I don't know what good it would do :)

(I just renamed mine to test and everything worked fine)

---

### Post by qarews on 2007-08-16
thank you, that did the trick

but now i have another problem
i cannot install or remove any software .... same with updates

---

