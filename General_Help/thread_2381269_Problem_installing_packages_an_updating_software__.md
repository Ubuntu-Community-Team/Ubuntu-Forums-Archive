---
title: "Problem installing packages an updating software  -Python error"
date: 2017-12-29
forum: General Help
---

### Post by ianfego on 2017-12-29
Hi everyone. im a new user of ubuntu and a new user of this forum and i would appreciate if someone can help me. I have the version 16.04.My problem is next one: as an example if i try to install vlc package i get this error:
```

installArchives() failed:  Extracting templates from packages: 93%% Extracting templates from packages: 100%% 
 Extracting templates from packages: 93%% Extracting templates from packages: 100%% 
 Extracting templates from packages: 93%% Extracting templates from packages: 100%% 
dpkg: error processing package python3.5-minimal (--configure): 
 package is in a very bad inconsistent state; you should 
 reinstall it before attempting configuration 
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of python3-minimal: 
 python3-minimal depends on python3.5-minimal (>= 3.5.1-2~); however: 
  Package python3.5-minimal is not configured yet. 
 
dpkg: error processing package python3-minimal (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 python3.5-minimal 
 python3-minimal 
dpkg: error processing package python3.5-minimal (--configure): 
 package is in a very bad inconsistent state; you should 
 reinstall it before attempting configuration 
dpkg: dependency problems prevent configuration of python3-minimal: 
 python3-minimal depends on python3.5-minimal (>= 3.5.1-2~); however: 
  Package python3.5-minimal is not configured yet. 
 
dpkg: error processing package python3-minimal (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python3.5: 
 python3.5 depends on python3.5-minimal (= 3.5.2-2ubuntu0~16.04.4); however: 
  Package python3.5-minimal is not configured yet. 
 
dpkg: error processing package python3.5 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python3: 
 python3 depends on python3.5 (>= 3.5.1-2~); however: 
  Package python3.5 is not configured yet. 
 python3 depends on python3-minimal (= 3.5.1-3); however: 
  Package python3-minimal is not configured yet. 
 
dpkg: error processing package python3 (--configure): 
 dependency problems - leaving unconfigured
```

---

### Post by ian-weisser on 2017-12-29
Why did you destroy or damage your Python 3.5?
What were you trying to accomplish?

---

### Post by ianfego on 2017-12-29
I don't really know how, is there any way to repair all of this?

---

### Post by ian-weisser on 2017-12-29
I'm curious *why* you did it. You may have done lots of other kinds of damage, and you might promptly do it again.

How to fix it is pretty easy:
Start by re-installing the package, just like the error message instructed.
Since apt requires python to work, let's use dpkg:

Step 1: Look in /var/cache/apt/archives for your python3.5-minimal package.
If it's there, write down the EXACT complete package name.
If it's not there, download it from [http://packages.ubuntu.com](http://packages.ubuntu.com) and put it there.

Step 2: Use dpkg to re-install the package
```
sudo dpkg --install /var/cache/apt/archives/<exact_package_name>.deb
```

If it doesn't seem to work, or if it throws errors, then please show us the complete output of the dpkg session.

---

### Post by ianfego on 2017-12-29
it worked  just fine,thank you. And answering to your "why", i didn't have any intentions of damaging python or anything else, what could have been the cause?.

---

### Post by ian-weisser on 2017-12-29
Few 'intend' to cause damage. It usually happens while en route to a different goal.
There are many, many possible direct causes. Insufficient data to localize one.
It usually requires the use of sudo. It often involves following random instructions from the dirty, dirty internet.

Or blame the family pet.

---

### Post by ianfego on 2017-12-29
Well I'll try to be more careful, thanks for your help.

---

