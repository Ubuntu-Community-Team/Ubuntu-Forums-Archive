---
title: "splashscreens"
date: 2008-05-20
forum: General Help
---

### Post by AznPat on 2008-05-20
can anybody give me the steps on how to set up an splash screen..i m really new to ubuntu.thanks

---

### Post by Patb on 2008-05-20
AznPat, splash screens are usually specific to the application.  You would probably have to look up the documentation for the particular application you are interested in.  

If you mean the splash screen for login, Ubuntu has several themes.  Start Synaptic and look for usplash.  

Cheers, Pat.

---

### Post by Exsecrabilus on 2008-05-20
Try doing:

```
sudo apt-get install gtweakui startup-manager
```

Gtweak UI for managing Splash themes, and StartUp-Manager for managing USplash themes.

---

### Post by AznPat on 2008-05-21
i wrote the code that u told me but it says E: couldn't find package start-up manager..

---

### Post by Exsecrabilus on 2008-05-22
I'm sorry, I messed up the name.

Try this code in the Terminal:

```
sudo apt-get install gtweakui startupmanager
```

After installation, go **System** >> **Preferences** >> **gTweakUI - Session**.
It will say something about no splashscreen; ignore it.

Check the box that reads *Show splash screen on login* then click the giant box.
It will automatically open up a search box to search for the splash image.

---

