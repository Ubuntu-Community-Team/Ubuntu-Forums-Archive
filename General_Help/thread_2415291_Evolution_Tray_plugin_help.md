---
title: "Evolution Tray plugin help"
date: 2019-03-23
forum: General Help
---

### Post by mikeebean on 2019-03-23
I've just installed Evolution as a replacement for Sylpheed in Lubuntu. Sylpheed had the built-in option to minimize to tray. Evolution doesn't have this function, but there is a plugin called Evolution Tray to accomplish the same. 

However when I try to install it, I get an error that the directory 'evolution-plugin-3.0" could not be found. Looking around, I see that there's a 'plugins' folder in usr/lib/evolution. I tried creating a folder there with the name the installer is looking for, but the installer doesn't see it because the new folder isn't registered with the system.

I'm guessing that Evolution has changed the name of the plugins folder... If this is the case, how can I update the installer script to look for the correct directory, or can I somehow create the expected directory for the installer and move the plugin data after it finishes?

---

