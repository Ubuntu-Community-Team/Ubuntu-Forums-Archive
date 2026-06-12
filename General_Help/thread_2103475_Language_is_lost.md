---
title: "Language is lost"
date: 2013-01-10
forum: General Help
---

### Post by mquintus2 on 2013-01-10
Ahoy mates,

after a hard shutdown (Ubuntu stopped to warn me about flat batteries aprx. 1 year ago) after the restart my language settings are set to somewhat chinese i guess. 
It's fun to see all those weird letters. :popcorn: 

For now it's enough. How can I set my "linux for human beings" back to german?

See the pictures ;)

Best,
Marius

---

### Post by mquintus2 on 2013-01-10
I am using Ubuntu 12.10, fresh install, 64bit, w/ encrypted hard drive an a Lenovo T430s.

```
$ locale
LANG=zh_CN.UTF-8
LANGUAGE=zh_CN:de_DE:en
LC_CTYPE="zh_CN.UTF-8"
LC_NUMERIC=de_DE.UTF-8
LC_TIME=de_DE.UTF-8
LC_COLLATE="zh_CN.UTF-8"
LC_MONETARY=de_DE.UTF-8
LC_MESSAGES="zh_CN.UTF-8"
LC_PAPER=de_DE.UTF-8
LC_NAME=de_DE.UTF-8
LC_ADDRESS=de_DE.UTF-8
LC_TELEPHONE=de_DE.UTF-8
LC_MEASUREMENT=de_DE.UTF-8
LC_IDENTIFICATION=de_DE.UTF-8
LC_ALL=

$ export LC_ALL=de_DE.utf8
$ export LANG=de_DE.utf8
$ export LANGUAGE=de_DE.utf8

```did't help

---

### Post by dino99 on 2013-01-10
use the System Settings -> language icon menu :

set your prefered language on top of the list, then hit "apply to the whole system"

do the same for your "local language"

then logout/in ; if you still have that issue, then reboot. If its not resolved, then create a new user.

---

