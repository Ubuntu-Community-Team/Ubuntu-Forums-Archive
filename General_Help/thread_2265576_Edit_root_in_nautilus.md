---
title: "Edit root in nautilus?"
date: 2015-02-16
forum: General Help
---

### Post by petermartin2 on 2015-02-16
Once in a while I find myself in a situation where I need to edit root. Sometimes I feel the urge to do this in nautilus but I can't. I've read that some versions of Ubuntu have an "open as administrator" option on right click in nautilus but I don't (14.10). Is there anyway to move things to and from root, edit and delete etc in nautilus or do I have to go through terminal?

---

### Post by Frogs Hair on 2015-02-16
AFIK the terminal with a password prompt is the only option, this is a security measure to protect the file system from tampering.

---

### Post by grahammechanical on 2015-02-16
```
sudo -H nautilus
```

will give us the power to use the nautilus file manager to usefully access system folders as well as breaking the system. In the past we could use

```
gksudo nautilus
```

But gksu is no longer installed by default. It has been depreciated by the developers and one day may not be available to install. But we can still install gksu

```
sudo apt-get install gksu
```

When using gksudo to open nautilus there will be error messages. Ignore them. Each of these commands can only be run by the user who has administrator privileges. So, security is still preserved.

Regards.

---

### Post by petermartin2 on 2015-02-16
> **grahammechanical said:**
> ```
sudo -H nautilus
```

will give us the power to use the nautilus file manager to usefully access system folders as well as breaking the system. In the past we could use


Uh once I shut down nautilus again everything will be back to normal right?

---

