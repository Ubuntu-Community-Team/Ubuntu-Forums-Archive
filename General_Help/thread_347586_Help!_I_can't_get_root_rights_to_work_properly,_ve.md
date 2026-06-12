---
title: "Help! I can't get root rights to work properly, very frustrating"
date: 2007-01-27
forum: General Help
---

### Post by stephentyler20 on 2007-01-27
I posted this last night, but received no helpful responses. When I try to do anything with regard to gksudo, such as alt-F2 gksudo nautilus, or gksudo gedit /etc/bluetooth/hcid.conf, the desired file takes FOREVER to open. So long, in fact, that it would make routine editing of such files extremely frustrating, and not worth my time. For example, five minutes ago, I typed "gksudo gedit /etc/bluetooth/hcid.conf" into the terminal window. The gedit program opened, and hung for about 5 minutes, and just now displayed the text. Otherwise, I would have had to force-quit the application. 

What can be done to diagnose/fix this program? I'm still quite new to Ubuntu. It's not the problem itself that troubles me that much, but rather the fact that it came up without me doing anything outrageous to cause it (I'm just trying to get the laptop up and running on Ubuntu). Frankly, if I can't resolve this, it might scare me back over to windows, however reluctantly.

EDIT: my mistake, I did receive one helpful response with how to use nano to edit the files, but this doesn't fix my problem, so I'm looking for more help.

---

### Post by taurus on 2007-01-27
Stick with "sudo nano" for now and forget about "gksudo gedit", okay.

---

### Post by stephentyler20 on 2007-01-27
> **taurus said:**
> Stick with "sudo nano" for now and forget about "gksudo gedit", okay.

I appreciate that nano works, but how can you consider ignoring the problem to be a solution? If there's such an absurd delay there, that to me indicates that there is a deeper problem somewhere else, that may manifest itself in another fashion at a later time. I'm not prepared to deal with such a problem by just ignoring it.

---

### Post by Patrick-Ruff on 2007-01-27
kind of sad how people are so addicted to the GUI . . . windows is a disease.  my oh my I wish my laptop was on an nVidia card.

what are your specs?

---

### Post by stephentyler20 on 2007-01-27
> **Patrick-Ruff said:**
> kind of sad how people are so addicted to the GUI . . . windows is a disease.  my oh my I wish my laptop was on an nVidia card.

what are your specs?

Again, it's not that I'm "addicted" to the GUI, I just can't understand how the existence of a problem isn't something I should worry about fixing.

I'm running Ubuntu 6.10, I have a Core Duo processor at 2ghz, 60 gig HD dual booting Windows XP (I'm not letting go just yet).

---

### Post by Patrick-Ruff on 2007-01-27
uh huh. anyways, it's possible that your computer may not be using both cores of your processor, but as far as solving that I have no idea.

---

### Post by stephentyler20 on 2007-01-27
It's using both cores, I'm confident of that. Nothing else in the system runs slowly, just the gedit function. Everything else works just fine.

---

### Post by Tomosaur on 2007-01-27
Interesting problem, but the solution could lie in any number of places. Try:
```

sudo aptitude reinstall gedit

```

Could have been a dodgy installation, however unlikely. If that doesn't solve the problem, which kernel are you using? Your setup would benefit from the 'generic' kernel. This used to be the kernel version optimised for dual or multi-core processors, but they changed the name. If your kernel version doesn't have 'generic' in the title, you should install the latest generic version.

---

### Post by taurus on 2007-01-27
Does it run slow or delay with

```
gedit ~/.bash_profile
```

---

### Post by stephentyler20 on 2007-01-27
> **taurus said:**
> Does it run slow or delay with

```
gedit ~/.bash_profile
```

No, it does not. Does that mean anything?

---

### Post by stephentyler20 on 2007-01-27
> **Tomosaur said:**
> Interesting problem, but the solution could lie in any number of places. Try:
```

sudo aptitude reinstall gedit

```

Could have been a dodgy installation, however unlikely. If that doesn't solve the problem, which kernel are you using? Your setup would benefit from the 'generic' kernel. This used to be the kernel version optimised for dual or multi-core processors, but they changed the name. If your kernel version doesn't have 'generic' in the title, you should install the latest generic version.

I did the reinstall, and it still hangs. I checked and I am using a generic kernel. Any other tips?

---

### Post by taurus on 2007-01-27
How about 

```
gksudo nautilus
-or-
gksudo synaptic
```

---

### Post by stephentyler20 on 2007-01-27
gksudo nautilus DOES hang, have not tried synaptic yet

---

### Post by taurus on 2007-01-27
Are you running x86 or x86_64?

```
uname -a
```

---

### Post by stephentyler20 on 2007-01-27
x86. At this point, the problem seems to have gone away. I don't know why, but I think it might have been related to Network-manager, as when I removed network-manager from my system, the problem apparently resolved. 

I have switched back to Wifi radar, which works a little better for me anyway.

---

