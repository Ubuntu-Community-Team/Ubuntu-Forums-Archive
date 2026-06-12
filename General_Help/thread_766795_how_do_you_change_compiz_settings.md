---
title: "how do you change compiz settings"
date: 2008-04-25
forum: General Help
---

### Post by YonyonJohn on 2008-04-25
sorry to be asking such a stupid question, but I cant find any menu or app to configure compiz fusion on hardy heron. does anyone know where I could find such a tool?

---

### Post by sisco311 on 2008-04-25
Install the compizconfig-settings-manager package from Synaptic or Add/Remove Programs.
Or use the terminal:
```
sudo aptitude install compizconfig-settings-manager
```

---

### Post by issih on 2008-04-25
I got caught out by this too, for hardy you need to install the package 'simple-ccsm', either via synaptic or apt-get, this will then add the 'custom' option to the visual effects tab of appearance preferences.

The Simple-CCSM is rather limited in what it will let you do, it is what it claims to be, a simple compiz config settings manager, allowing you to fiddle with some of the more well known effects without having to tweak lots of parameters individually. It is clearly designed to present new users with a less daunting experience.

If you (like me) are used to playing with the full blown ccsm from using gutsy, it will probably seem rather restrictive, fortunately, once you have 'simple-ccsm' installed and have selected 'custom' in the visual effects tab, you can still use the old full fat ccsm to tweak away to your hearts content, just install 'compizconfig-settings-manager' if its not installed already and fire up Advanced Desktop Effects Settings from the System->Preferences menu.

N.B. you need simple-ccsm installed to be able to select the custom option, installing the full blown ccsm on its own doesn't seem to work..at least not for me

Hope that helps

---

### Post by YonyonJohn on 2008-04-25
thanks, but every time I try to install it, it says downloading for a while and then says that the servers can't be contacted. is there any way to fix this or should I just wait it out?

never mind, it worked on the third try :P

---

### Post by Arlanthir on 2008-04-25
Note that you have to install simple-ccsm too:

```
sudo apt-get install simple-ccsm compizconfig-settings-manager
```

After that just go to System > Preferences > Appearance > Desktop Effects

Choose Custom and then use System > Preferences > Advanced Desktop Effects Settings to configure.

---

