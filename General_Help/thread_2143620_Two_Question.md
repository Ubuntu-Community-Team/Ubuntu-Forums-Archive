---
title: "Two Question"
date: 2013-05-09
forum: General Help
---

### Post by JonStyles on 2013-05-09
1) I was trying to install the MS truefont and i mistakely decline the terms or whatever and now i cant install. How can I fix this?

2) How to you get the scolling and tapping feature to stop on my touchpad on my laptop. it not even selected, everytime i type the page either scolls down or goes back. Any ideas

---

### Post by dino99 on 2013-05-09
1) reinstall the font : sudo apt-get install --reinstall  ttf-mscorefonts-installer

2) looks like you need to clean the touchpad (with a wet paper)

---

### Post by matt_symes on 2013-05-09
Hi

> **JonStyles said:**
> 1) I was trying to install the MS truefont and i mistakely decline the terms or whatever and now i cant install. How can I fix this?

Try this

From the terminal...

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Enter your password. It will not be echoed to the screen.

Post back any errors.

You could also try to reconfigure it using ```
sudo dpkg-reconfigure -phigh <package_name>
```

> 2) How to you get the scolling and tapping feature to stop on my touchpad on my laptop. it not even selected, everytime i type the page either scolls down or goes back. Any ideas

I suspect that you can disable it using the mouse/touchpad settings window.

Kind regards

---

