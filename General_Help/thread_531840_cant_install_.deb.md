---
title: "cant install .deb"
date: 2007-08-22
forum: General Help
---

### Post by vinogans on 2007-08-22
strange thing happen when i download .deb package some i see it and some doesnt appear any where tried to install same package with synaptic also the same , the package doesnt got any error i am sure coz one of them is wine 0.9.43 from their site so any idea to fix it notice that no where I mean also the application path

---

### Post by por100pre1 on 2007-08-22
Maybe WINE is installed but the launchers are missing. Try launching Wine configuration in terminal:

```
winecfg
```

For WINE file viewer:

```
winefile
```

For WINE software uninstaller:

```
uninstaller
```

If neither of these commands work then WINE is not installed. Hope this helps. :)

---

### Post by vinogans on 2007-08-22
> **por100pre1 said:**
> Maybe WINE is installed but the launchers are missing. Try launching Wine configuration in terminal:

```
winecfg
```

For WINE file viewer:

```
winefile
```

For WINE software uninstaller:

```
uninstaller
```

If neither of these commands work then WINE is not installed. Hope this helps. :)

wow it make wine run but the thing where is he ? :P now i can see the folder of it but what any way thanks for the tip i used the command to creat a launcher in application so i think no problem .. but do u got idea why this happen thanks man u helped me

---

### Post by por100pre1 on 2007-08-22
I think the WINE installer is not properly configured. I remember making the launchers myself, just like you did. Glad to help.
:popcorn:

---

