---
title: "VLC and Azereus crash as soon as open"
date: 2007-07-13
forum: General Help
---

### Post by iamlost on 2007-07-13
Hi,
When ever i open with VLC or Azereus they crash as soon as they open. I have no idea why they did used to load ok and now they crash everytime, i've tried opening on their own to see if any other programs effected them but nothing works. Any possible reasons and solutions to this annoying problem?

---

### Post by Happy_Man on 2007-07-13
Sometimes this happens, a solution I've always found effective is to just reboot the system and the problems generally go away.

---

### Post by iamlost on 2007-07-14
I have tryed rebooting it and nothing change they both still crash as soon as the load up. I even tried reinstalling the packages but that didn't fix the problem either.

---

### Post by Happy_Man on 2007-07-14
Did you delete the config folders? Open up your home folder, hit ctrl+H, and delete the .azureus and .vlc folders. Then open the programs again.

---

### Post by bsmith1051 on 2007-07-15
I'm having the same problem with Azureus 2.5.0.0 installed through Add/Remove.  I can delete the config folder and it will start-up again with the new user configuration wizard.  But it then self-destructs almost immediately.  I'm probably going to try uninstalling (using complete removal) and then install it manually...

P.S.  I'm running Ubuntu 7.04 with Sun Java 5 Web-plugin, then Sun Java 6 JRE installed, as well as the Nvidia video binary.

---

### Post by BoneSaw on 2007-07-15
try running the program in the terminal and pasting the output here.

i was having the same problem with azureus and remember there being two possible solutions, one being deleting the config files and i dont remember the other. try searching the forums maybe?

---

### Post by bsmith1051 on 2007-07-16
for the moment, I've downloaded the 2.5.0.4 installer, then copied the new 'Azureus2.jar' file over the original 2.5.0.0.  Seems to be working so far.  So maybe the Ubuntu repository needs to be updated?

---

### Post by melenor on 2007-07-18
> **bsmith1051 said:**
> for the moment, I've downloaded the 2.5.0.4 installer, then copied the new 'Azureus2.jar' file over the original 2.5.0.0.  Seems to be working so far.  So maybe the Ubuntu repository needs to be updated?

where do you copy the new 'Azureus2.jar' file to?

---

### Post by bsmith1051 on 2007-07-19
I inspected the properties of the shortcut, which led me to a simple script which in turn I was able to read and find the .jar in /usr/share/Java.  I had to use 'sudo mv' to rename the original file and then 'sudo cp' to copy the replacement.

---

