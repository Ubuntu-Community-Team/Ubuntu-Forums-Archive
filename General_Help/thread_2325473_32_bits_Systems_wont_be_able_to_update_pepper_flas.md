---
title: "32 bits Systems wont be able to update pepper flash player?"
date: 2016-05-22
forum: General Help
---

### Post by mario71 on 2016-05-22
So Google has dropped the support for 32 bits which isnt something new but since the flash player for Chromium and other Chromium based browsers such as Opera was obtained with the latest Chrome version.
now that it has been dropped i would like to know if im wrong but if I run on the terminal :

```
update-pepperflashplugin-nonfree --status
```

I get that the lastest version is 20.0.0.386 

Which is not completely outdated but whenever i try to access using Opera an object which requieres flash it says my version is outdated since the latest version is 21.0.0.242.

How can i fix this or flash content wont be available anymore with Chromium and derivatives?

I tried using firefox which seems to load the plugin but either using the latest version offered by Adobe (11...someting) or pepper 20.0.0.386 the performance is awful 
which was one of the reasons i switched to Opera but now i just realized that i cant use it with Opera which ran fine the last time i used it :|.

---

### Post by Dennis N on 2016-05-22
Install the package **adobe-flashplugin**. It continues to provide a 32-bit version of the flash player for Chromium. This works in Ubuntu and its family of distros. To install it, enable Canonical Partners in your software sources and reload. Then it will be available for installation.

---

### Post by mario71 on 2016-05-25
Thanks that did the trick , but i couldn't find where to change the repos from the ubuntu software center so i had to do it by uncommenting the canonical on sources.list.

---

