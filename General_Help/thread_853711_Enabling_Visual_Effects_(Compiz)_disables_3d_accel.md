---
title: "Enabling Visual Effects (Compiz?) disables 3d accelleration"
date: 2008-07-08
forum: General Help
---

### Post by Mecandes on 2008-07-08
This is odd. I'm running Ubuntu 8.04 with the normal nVidia x86 driver version 96.43.05. If I go to Appearance Preferences and enable Visual Effects, it works great: I get the transparency and stretchy effect and it runs perfectly well and fast, including things like Avant Window Navigator.

However, when Visual Effects are turned on (either "Normal" or "Extra"), all 3d accelleration stops working in games and things like GL XScreenSavers. (The graphics appear, but run at about 1 frame per 10 seconds.) Disabling the Visual Effects returns these things to full speed.

Just seems odd that either the window effects run great, or 3d games run great -- but not both?

---

### Post by paul101 on 2008-07-08
it seems to be a problem with some graphics cards



use the compiz fusion icon to quickly switch compiz on / off :)


(if you dont have it)
```
sudo apt-get install fusion-icon
```

[img]http://tombuntu.com/wp-content/uploads/2008/03/fusion-icon1.jpg[/img]


To start Fusion-icon whenever you log in, add it to the Startup Programs list in 

System->Preferences->Sessions.


[img]http://tombuntu.com/wp-content/uploads/2008/03/fusion-icon2.jpg[/img]

---

### Post by overdrank on 2008-07-08
> **Mecandes said:**
> This is odd. I'm running Ubuntu 8.04 with the normal nVidia x86 driver version 96.43.05. If I go to Appearance Preferences and enable Visual Effects, it works great: I get the transparency and stretchy effect and it runs perfectly well and fast, including things like Avant Window Navigator.

However, when Visual Effects are turned on (either "Normal" or "Extra"), all 3d accelleration stops working in games and things like GL XScreenSavers. (The graphics appear, but run at about 1 frame per 10 seconds.) Disabling the Visual Effects returns these things to full speed.

Just seems odd that either the window effects run great, or 3d games run great -- but not both?

Hi and just a quick question, why are you using the old driver, what is the model of the graphics card?

---

### Post by larryfroot on 2008-09-21
Thought I would bump this thread up as my issue is exactly the same. I have an ati HD 4870 running with the latest drivers (catalyst 8.9). All is well and dinky until I switch compiz on. I know about the fusion-icon trick, but would prefer to get to the bottom of it as I'm that type of person really. Symptoms of compiz buggering around with 3d acceleration are flickering followed by breaking up and no sign of any window decoration at all. Thanks for any pointers given!

---

