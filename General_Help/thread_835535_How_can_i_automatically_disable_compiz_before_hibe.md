---
title: "How can i automatically disable compiz before hibernation?"
date: 2008-06-20
forum: General Help
---

### Post by gsiliceo on 2008-06-20
This started happening in hardy, never happened in feisty nor gutsy.
If i hibernate with compiz enable when the pc come back its a white screen no mouse no desktop no nothing, i can ctrl+alt+del to restart X.

What i want to know is what script is used to hibernate that i can edit to automatically disable compiz, and the script used to come back from hibernation to automatically enable compiz again.

---

### Post by gsiliceo on 2008-06-21
huh hello?

---

### Post by PinkFloyd102489 on 2008-06-21
Try setting Xinerama to 0 in the xorg.conf.

---

### Post by sdennie on 2008-06-21
Have you tried entering your password into that white screen?  I think this is a common bug with nvidia drivers.  If that doesn't work, try something like this:

```

#!/bin/bash

XUSER=your_username

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
        DISPLAY=:0.0 su ${XUSER} -c "metacity --replace"
    ;;
    thaw|resume)
        DISPLAY=:0.0 su ${XUSER} -c "compiz --replace"
    ;;
    *)
    ;;
esac

exit

```

Call the script 99compiz.sh, change the username in "XUSER=username" to your username and then install the script with:

```

sudo install 99compiz.sh /etc/pm/sleep.d

```

Edit:
I haven't actually tried this but, I do similar things for power management.

---

### Post by gsiliceo on 2008-06-22
Thank you both, i'm not sure wich solution was the right one but i did it both, i don't need xinerama anyway(just 1 screen). 
=D

---

### Post by gsiliceo on 2008-06-23
MMM now this caused another problem, for some reason now every time i hibernate my home partition gets dirty and linux set it read mode only.
Its and ext3 partition, i have to restart and fsck it to make it writable again.
I cant event unmount it after hibernantion only restarting works, weird...

Update: turns out that my hard disk was faulty and it was getting dirty because of those errors, SMART warned me :P

---

