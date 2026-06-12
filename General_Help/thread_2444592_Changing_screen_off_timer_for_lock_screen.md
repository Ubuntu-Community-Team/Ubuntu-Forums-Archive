---
title: "Changing screen off timer for lock screen?"
date: 2020-06-01
forum: General Help
---

### Post by grandkodiak2 on 2020-06-01
Where can I adjust the screen timer for the lock screen? Doesn't matter either on battery or external power, I have all the options set to "never" but anytime I lock the laptop instead of the cool lock screen, it turns the screen off almost immediately. If I click to get the log in prompt, even that will turn off after a few minutes. Where can I change it to always simply display the lock screen and/or log in when not in use? Cant seem to find it anywhere so I'm assuming its in some archaic text somewhere in the file system gnome folders?

---

### Post by deadflowr on 2020-06-01
Which release of Ubuntu?
Afaik lock simply turns off the display.
Screensaver should able to be set to run in dconf-editor
(org > gnome > desktop > screensaver)

Something like this:
[http://ubuntuhandbook.org/index.php/2019/01/set-custom-blank-screen-lock-screen-time-ubuntu-18-04/]("http://ubuntuhandbook.org/index.php/2019/01/set-custom-blank-screen-lock-screen-time-ubuntu-18-04/")

There's also this about lock screen on 20.04
[https://askubuntu.com/questions/1230714/lock-screen-wallpaper-option-on-ubuntu-20-04-lts-is-not-available]("https://askubuntu.com/questions/1230714/lock-screen-wallpaper-option-on-ubuntu-20-04-lts-is-not-available")

---

