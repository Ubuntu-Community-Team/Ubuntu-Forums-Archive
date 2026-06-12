---
title: "Shutdown And Reboot Button Are Missing"
date: 2008-05-19
forum: General Help
---

### Post by leboea on 2008-05-19
I am using Ubuntu 8.04 LTS on Acer Aspire 5310. Everything worked fined at first(after the installation). I did several reboots and now I can't reboot because there is no reboot and shutdown button anymore. How to a get them back again?

---

### Post by y-lee on 2008-05-19
Right click the panel you wish to have the shutdown button and choose add to panel. In the window that pops up find the shutdown button and drag it to the panel and place it where you want it.

If this works or doesn't work let us know.

BTW there is a command to shutdown linux. Open a terminal (in Menu Under accessories) *OR* hit **Alt F2** and type

```
sudo shutdown -h now
```

This will ask you for your password, type it in and hit enter. NOTE your password will not be displayed as you type for security reasons, nothing to be worried about.

To reboot from the command line, type:

```
sudo shutdown -r now
```

---

