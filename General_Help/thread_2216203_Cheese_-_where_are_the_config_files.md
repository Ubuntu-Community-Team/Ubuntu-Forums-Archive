---
title: "Cheese - where are the config files?"
date: 2014-04-10
forum: General Help
---

### Post by Roasted on 2014-04-10
Let's say I change a preference under the Edit >> Preferences menu of Cheese. Where on earth do those settings get stored? How can I access them via terminal?

---

### Post by Impavidus on 2014-04-10
I don't know about cheese, but usually the setting would be stored in ~/.cheese (either a file or a directory) or ~/.config/cheese.

---

### Post by monkeybrain20122 on 2014-04-10
Apparently it doesn't store its configuration in a config file like ~/.cheese but in gsettings. So you have to access the settings with the dconf-editor.
[http://askubuntu.com/questions/233063/cheese-config-file-location](http://askubuntu.com/questions/233063/cheese-config-file-location)

---

### Post by Roasted on 2014-04-10
> **monkeybrain20122 said:**
> Apparently it doesn't store its configuration in a config file like ~/.cheese but in gsettings. So you have to access the settings with the dconf-editor.
[http://askubuntu.com/questions/233063/cheese-config-file-location](http://askubuntu.com/questions/233063/cheese-config-file-location)

:guitar::guitar:

---

