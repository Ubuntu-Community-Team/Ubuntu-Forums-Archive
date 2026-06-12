---
title: "Login screen to operate without mouse"
date: 2016-10-04
forum: General Help
---

### Post by VictorR on 2016-10-04
Is there any login screen I could operate - change user, select session, navigate etc., with keyboard only?

The reason behind the question is that I have a KODIbuntu media center, its underlaying OS is Lubuntu 14.04 LTS. The baby low-power computer is hidden behind the TV set. It's controlled with a wireless full QWERTY keyboard the size of a remote control with tiny touch-pad. Kodi is designed to work well without mouse; in Lubuntu I can do stuff with keyboard only as well. To switch between Kodi (one session) and Lubuntu (another session) I have to log out, select another session, and log in - and this is real pain, touch-pad does not work there. There are dozens login screens to select in Lubuntu itself and thousands on sites like Gnome-look.org, but their authors concentrate on visual appearance rather than usability.

Does anybody can point to a login screen which allows easy navigation with keyboard only? I am not concerned about its look.

Thank you.


It's solved. After looking into GDM screens I found they are plain XML files without any reference to keyboard shortcuts. So I just logged out in my Kodibuntu (which is stripped to the bone Lubuntu version) and start pressing all keys on the keyboard. Surprisingly ESC moved focus to the action area, so I found how to navigate in the login screen without mouse. I also noticed that some GDM screens have acceleration characters (underscored letters).

---

