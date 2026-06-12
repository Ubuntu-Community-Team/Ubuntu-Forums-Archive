---
title: "Run command on logout -espeak"
date: 2014-04-13
forum: General Help
---

### Post by Tristan_Williams on 2014-04-13
I want to run something like 'espeak "goodbye"' whenever someone logs out.

I tried putting it in ~/.bash_logout but it doesn't work.

What can I do?

---

### Post by grumblebum2 on 2014-04-14
This worked for me on 14.04.
Created an espeak script...
```
#!/bin/bash
/usr/bin/espeak "Goodbye $USER"
```

Then edited /etc/lightdm/lightdm.conf...
```
gksudo gedit /etc/lightdm/lightdm.conf
```

and added...
```
[SeatDefaults]
session-cleanup-script=/home/glen/scripts/espeak-goodbye.sh

```
Use your own full path to script.

---

