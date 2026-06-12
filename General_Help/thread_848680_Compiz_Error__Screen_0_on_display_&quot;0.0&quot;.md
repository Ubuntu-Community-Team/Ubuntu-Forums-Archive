---
title: "Compiz Error : Screen 0 on display &quot;:0.0&quot;"
date: 2008-07-03
forum: General Help
---

### Post by Skelly on 2008-07-03
Hi, I'm a relatively new Ubuntu user and I've recently had problems with Compiz.

the main problem is that once i activated the Advanced Desktop effects, all of the compiz features were deactivated but i can still turn features on and off in the menu, with no physical effect. through terminal I receive this:

```
- Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0
```

and after trying several methods to resolve this, I still have no result.

So i decided to start fresh and get rid of Compiz and reinstall it, this is the main problem, that after removing all copies of Compiz using the Synaptic manager I'm still able to open up the Compiz menu and also the Emerald Menu, even though according to Synaptic they dont exist.

Also, i did a search for "Compiz" through all folders on my system and it returned around 550 results.

1/. Is it possible there is another copy of Compiz / Emerald embedded in the system, if so how do i get rid of them?

2/. Is there a simple fix I'm missing somewhere

3/. Any suggestions are greatly appreciated

Cheers

---

### Post by cobra1984 on 2011-04-21
I had this same problem but realized it doesn't necessarily mean anything in regards to your desktop effects as i have a DELL 630 laptop running perfectly fine with this message. I'm trying to get to the bottom of why I don't have the ability to use effects on my desktop computer. It appears it could be a driver compatibility issue with the Nvidia Geforce 8400gs card i have.:confused:

---

### Post by mcduck on 2011-04-21
> **Skelly said:**
> 
the main problem is that once i activated the Advanced Desktop effects, all of the compiz features were deactivated[/CODE]



Just to make sure, have you tried installing Compiz yourself, possibly from some other source than from ubutnu's repositories?

The "Advanced Destop Effects" in Ubuntu *is* Compiz, and it's installed by default.

The options in the Appearance settings switch between Metacity ("None") and two pre-configured Compiz configurations ("Normal" and "Extra"). If you then change any Compiz settings yourself you aren't running any of the preset configurations, on some Ubuntu versions this will show as "Custom" option, while on others simply by none of the settings in the Appearance dialog being selected.

Anyway, your error message is telling you that to run a window manager you can't just use the window manager's name, but instead you need to dd the "--replace" option to tell it to replace whatever window anager you are using at the moment. For example "compiz --replace" or "metacity --replace".

---

