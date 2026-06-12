---
title: "Serial"
date: 2016-01-22
forum: General Help
---

### Post by bradynbouchard on 2016-01-22
I am planing on getting a computerized telescope but I can't figure out how the serial com port number I want to get a Celestron cbc deluxe 1100 telescope and connect it to my and computer and the program stellarium

---

### Post by Nuno_Abreu on 2016-01-22
I never had an experience with such a problem, but I gave it a search. Check this out:
[http://www.stellarium.org/wiki/index.php/Telescope_Control_plug-in#Device_settings](http://www.stellarium.org/wiki/index.php/Telescope_Control_plug-in#Device_settings)

Also, I couldn't know what Serial port number would be compatible with it. Like the above website says, you should run this command on the Terminal to (probably) check its number:

```
ls /dev/* | grep serial
```

After typing this command, you might see something. I added the **grep serial** myself, as it would be much easier for you to check from the list.

---

