---
title: "problem adding keybourd layout workaround to startup"
date: 2008-07-07
forum: General Help
---

### Post by pol-kilo on 2008-07-07
I have the bug with the keyboard that I can't switch layouts after reboot, I found this workaround script :

```
#!/bin/bash
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/options -t list --list-type=string "[]"
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/options -t list --list-type=string "`echo -e "[grp\tgrp:alt_shift_toggle]"`"
```

 Named it "keyfix" and put it in /usr/sbin, than I added it to "sessions" so it will fix it automatically at startup, but it doesn't work :(

(the script itself works great, but doesn't start with ubuntu)

---

### Post by iaculallad on 2008-07-07
Drop to your terminal and immediately change directory to /usr/sbin


```
cd /usr/sbin
```

Now, create your **keyfix.sh** file:

```
gksudo gedit /usr/sbin/keyfix.sh
```

Then place the script you created inside the file:

```
#!/bin/bash
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/options -t list --list-type=string "[]"
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/options -t list --list-type=string "`echo -e "[grp\tgrp:alt_shift_toggle]"`"
```

Save it and make it executable.

```
sudo chmod +x /usr/sbin/keyfix.sh
```

And, add it to your Sessions startup.

---

### Post by pol-kilo on 2008-07-07
Thank's for the replay, I did what you told, but I'm afraid it didn't work =(, any other ideas?

---

