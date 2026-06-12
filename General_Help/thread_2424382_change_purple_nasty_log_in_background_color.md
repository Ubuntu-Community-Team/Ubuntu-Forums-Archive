---
title: "change purple nasty log in background color?"
date: 2019-08-07
forum: General Help
---

### Post by grandkodiak2 on 2019-08-07
Is there a way to change the nasty purple orange whatever color ubuntu uses for its log in screen and logo? it's hideous and offensive to the eyes lol.

---

### Post by cruzer001 on 2019-08-07
I assume you mean GDM themes.  Haven't used any of these myself.

[https://www.gnome-look.org/browse/cat/131/](https://www.gnome-look.org/browse/cat/131/)

---

### Post by grandkodiak2 on 2019-08-07
found half of it, but it doesnt work... and i really meant also the splash boot screen with the Ubuntu and 5 dots screen too...

[URL="https://vitux.com/how-to-change-login-lock-screen-background-in-ubuntu/"]https://vitux.com/how-to-change-login-lock-screen-background-in-ubuntu/
[/URL]

---

### Post by cruzer001 on 2019-08-07
> i really meant also the splash boot screen with the Ubuntu and 5 dots screen too...
I believe you then want "plymouth themes ubuntu".  Try searching that.

I did try the css code and now have a GDM custom background and it is a nice touch.  Thank you :)

---

### Post by again? on 2019-08-07
_For plymouth splash screen_
```
sudo apt install plymouth-theme-ubuntu-gnome-logo
sudo update-alternatives --config default.plymouth
```
Choose **ubuntu-gnome-logo.plymouth**

_For the greeter/login_
```
sudo apt install --no-install-recommends gnome-session
sudo update-alternatives --config gdm3.css
```
Choose **gnome-shell.css**

You may still see a flash of purple just before the desktop loads.
If that annoys you can use the GNOME session as default and configure  to run like Ubuntu session.
I no longer use gnome-shell so don't know if there is an easier solution.

---

