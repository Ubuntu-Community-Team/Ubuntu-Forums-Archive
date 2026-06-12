---
title: "Disable log in after screen blanks out"
date: 2020-10-04
forum: General Help
---

### Post by Dan_Bowser on 2020-10-04
Hello,

I updated to xubuntu 20.04 a few days ago and since then every time the screen blanks out (by idle time) the OS requires a log in.

I want the blank out of the monitors but I don't want to have to log in every time.

I went to Xfce Power Manager through the settings menu and set Security to never lock the session. I also disabled (in the Display power management window) sleep/power off on idle. The behaviour persists after these changes.

I checked also xfce4-power-manager: dpms-enabled is set to true, and no other relevant looking option is toggled.

How do I stop the OS from requesting a log-in after blanking the screen?

Regards

---

### Post by randlieb on 2020-10-17
I had the same issue after the same upgrade.

Go to your settings and find 'users and groups'. Click on 'change' for your 'password'. Check the box marked 'don't ask for password on login'. That worked for me. [B]This will also allow no login upon boot, so if you don't want that, this method isn't what you want.

[/B]However I can not get my screen to blank. Have 'power settings' set to 'display' > 'blank after 15 minutes'. 'Security' is set to 'automatically lock session' > 'never'.

---

### Post by &amp;KyT$0P# on 2020-10-17
In Xubuntu 20.04 this is controlled in Settings > Screensaver unless you have explicitly set up light-locker.

---

