---
title: "Setting up 'headless' instance of 12.10"
date: 2013-05-08
forum: General Help
---

### Post by emaag on 2013-05-08
Hello everyone,

I've looked around everywhere and have found instructions for 12.04 but these were not applicable to 12.10. I have Ubuntu set up in a virtual machine and I am using it as my development environment. I do not need the GUI since I am logging in via SSH and was wondering how I go about setting it up so that I do not have the graphical elements load on boot, but rather it just going to a text only version. It tried following older instructions about setting the run level, but those do not seem to work with this version. Any help / guidance would be greatly appreciated.

Thank you,
Eric

---

### Post by cool110 on 2013-05-08
The easiest way would be to install the server edition.

---

### Post by Cheesemill on 2013-05-08
You can disable LightDM from automatically running when the system boots by doing...
```
echo "manual" | sudo tee -a /etc/init/lightdm.override
```

The system will then boot in CLI mode, if you want to start a GUI then just use the command...
```
startx
```

---

