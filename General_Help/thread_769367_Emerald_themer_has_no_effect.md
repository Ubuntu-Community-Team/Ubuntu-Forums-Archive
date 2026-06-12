---
title: "Emerald themer has no effect"
date: 2008-04-26
forum: General Help
---

### Post by nir78 on 2008-04-26
Hello,

I am using a clean install of 8.04 and try to use the emerald themer to configure the windows decoration (as I always did in earlier versions).

For unknown reason, this has no effect on the way my system looks! why is it? did I do something that disable the emerald tool ?

Please assist...
Nir

---

### Post by mecanologo on 2008-04-26
Same problem here...
I may change it after selecting the one I want, and then going to a terminal and writing emerald --replace 
but...
when I close the terminal, the title bar disappears.
any solution?

---

### Post by dwarness on 2008-04-26
I had this issue, but it's corrected easily.  Goto System->Preferences->Sessions

From the Startup Programs tab, just add a new entry with "emerald --replace" as the command.  Voila, emerald runs when you log in.

---

### Post by overdrank on 2008-04-26
> **mecanologo said:**
> Same problem here...
I may change it after selecting the one I want, and then going to a terminal and writing emerald --replace 
but...
when I close the terminal, the title bar disappears.
any solution?

HI and use the alt, F2 keys and use the ```
emerald --replace
```
You can also add it to the sessions under system, preference.

---

### Post by bonzini on 2008-04-27
So should one infer from this need to put "emerald --replace" in the startup menu that something is amiss with the way emerald is installed?

---

### Post by nir78 on 2008-04-27
Thanks for the answers...
Try this as soon as I get home.

Nir

---

### Post by darkoz on 2008-04-27
Hi there, 

I had this same problem and searching around the forum yielded the following:

1. Install compizconfig-settings-manager in Synaptic
2. Go to System -> Preferences -> Advanced Desktop Effects Settings
3. Click on "Window Decoration" in Effects section
4. replace whatever you have in the "Command" textbox with "/usr/bin/emerald --replace"
5. restart (or type "(emerald --replace &)" in terminal if you don't want to restart)

All good
Darko

---

### Post by darkoz on 2008-04-27
Forgot to mention that you can remove your Session start up entry if you follow the above instructions.

---

