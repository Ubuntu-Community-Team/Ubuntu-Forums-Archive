---
title: "gnome-terminal, shell script crash and relaunch but how?"
date: 2017-06-12
forum: General Help
---

### Post by KillerKelvUK on 2017-06-12
Hi, I'm running 16.04.2 with unity DE and have a shell script that runs on login.  The script effectively opens a terminal and runs an app and the apps stdout just sits there and scrolls doing its thang, however the app crashes sporadically (separate issue) so it needs to be relaunched.

```

#!/bin/bash
/usr/bin/gnome-terminal --window-with-profile=mining -e "/home/xxx/cpp-ethereum/build/ethminer/ethminer -U -S eth.pool.minergate.com:45791 -O xxx"

```

I'm using the code above in the startup script which works a treat and when the app crashes the terminal detects this and provides a GUI button to "Relaunch", how can I automate the relaunch?  I can't see any further application parameters for gnome-terminal, is there a simple way I can achieve this without having to deploy new packages?  I'm keen to learn here and my searches have yielded lots of solutions like separate supervisor packages or using systemd which I'll explore, I'm just wondering if I'm missing a simpler trick?

Thanks.

---

