---
title: "superkb fails to start"
date: 2016-04-19
forum: General Help
---

### Post by saint-u on 2016-04-19
Hello everybody, I am using Ubuntu 15.

I tried the program superkb (in order to find a lineakd replacement) but it fails to start with this error:

```
saint@t65:~
17:57:55 [5] $superkb 


superkb 0.23: Welcome. This program is under development.


It's strongly recommended to set the following on xorg.conf:


| Section "ServerFlags"
|   Option "AllowDeactivateGrabs" "On"
|   Option "AllowClosedownGrabs" "On"
| EndSection


With these, if the program fails while drawing the keyboard, you  will be able
to kill it by pressing Ctrl-Alt-*, and restore Autorepeat with 'xset r on'.


Error loading imagelib imlib2: //usr/lib//superkb/puticon-imlib2.so: undefined symbol: imlib_load_image
Failed to initialize image library: imlib2.


You might try any of the following as the value for IMAGELIB in
your $HOME/.superkbrc file: gdkpixbuf imlib2 



```

imlib2 is correctly installed.

Has anybody experienced the same problem and can someone tell me whether there is a solution or I should fill a bug report?

Thank you in advance.

---

