---
title: "Synaptic is choking"
date: 2007-06-27
forum: General Help
---

### Post by Ryzol on 2007-06-27
Went to run it and got this message:
```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'
```

For the record the last thing I had done was try to install [virtualbox]("http://www.virtualbox.org/wiki/Downloads"), after two hours of it not being done I tried to cancel the installation, it didn't let me and I couldn't determine which process to kill so I shutdown the computer.

---

### Post by FuturePilot on 2007-06-27
It seems that since it was shutdown in the process of installing it has been half installed or corrupted. You might want to download the deb again and try reinstalling it.

---

### Post by Ryzol on 2007-06-28
Just tried that. Gave me this error message:
```
Could not open 'virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb'

The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
```
I have full permissions on this file and I've downloaded it multiple times, surely they can't all be corrupted?

---

### Post by nutz on 2007-06-28
[http://www.ubuntugeek.com/package-installation-error-and-solution.html#more-35](http://www.ubuntugeek.com/package-installation-error-and-solution.html#more-35)

---

### Post by nutz on 2007-06-28
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by Ryzol on 2007-06-28
That worked, thanks a ton. :)

---

### Post by nutz on 2007-06-29
> **Ryzol said:**
> That worked, thanks a ton. :)

No problem, I ran into that same issue just a few days ago so it was still fresh in my mind. Glad I was able to help.

---

