---
title: "Small ET script"
date: 2007-04-04
forum: General Help
---

### Post by the slayer on 2007-04-04
Ive been playing some ET(Enemy territory) but ive got to make a little workaround before i get sound([http://katanoon.nl/ubu-e/install.php)(step](http://katanoon.nl/ubu-e/install.php)(step) 4)
But i want to make a script, that takes care af that for me:
[I]#!/bin/bash

ROOT_UID=0
E_NOTROOT=67
ged=et

if [ "$UID" -ne "$ROOT_UID" ]
then
   echo "Must be root to run this script."
   exit $E_NOTROOT
fi

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 

$"su peter"

"killall esd"


"et"[/I]


But it dont work, could you please help me?

---

### Post by mahy on 2007-04-04
I solved it by creating a file named .asoundrc in my home directory with the following content:

pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}

---

### Post by the slayer on 2007-04-04
Wow Thanks!!

---

