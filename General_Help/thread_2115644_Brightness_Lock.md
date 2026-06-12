---
title: "Brightness Lock"
date: 2013-02-13
forum: General Help
---

### Post by dlarkinator on 2013-02-13
I can manually turn the brightness down, but in 30 seconds it brightens itself again. How do I lock the brightness at a low setting?

---

### Post by pqwoerituytrueiwoq on 2013-02-13
if this command works this script will solve your issue

```
echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness
```[http://pastebin.com/HzzHrS2g](http://pastebin.com/HzzHrS2g) (use keyboard shortcut to call script commands)
i had to take "actual_" out of line 7 after a bios update

edit:
also try disabling dim screen after x second in the power manager

---

