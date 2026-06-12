---
title: "smartctl isn't showing in terminal"
date: 2015-08-25
forum: General Help
---

### Post by Rolandl on 2015-08-25
I have just updated the SMART pkgs in my Ubuntu 15.04 OS.
I restarted and entered [COLOR=#333333][FONT=UbuntuMono]sudo smartctl -i /dev/sda in terminal.
This came up: [/FONT][/COLOR]smartctl: command not found
I want to test the harddrive.
Any suggestions much appreciated.
:confused:

---

### Post by sudodus on 2015-08-25
I think you need to install smartmontools:

```
sudo apt-get install smartmontools
```

Then your command should work as well as with other options that you find in the manual

```
man smartctl
```

---

