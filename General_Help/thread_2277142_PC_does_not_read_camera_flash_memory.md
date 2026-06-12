---
title: "PC does not read camera flash memory"
date: 2015-05-07
forum: General Help
---

### Post by palmgrower on 2015-05-07
I have 2 PC's. Both on Ubuntu 15.04. One PC reads camera memory card no problem. Once connected, what-to-do window pops up. The other does nothing. I run disk utility (top left ubuntu icon > disk), but camera memory is not even recognized. Why the difference?

---

### Post by ajgreeny on 2015-05-07
Pop the card into the machine that does not find and open it and run command ```
sudo parted -l
``` which should show it listed as a separate drive; if it is not showing we need to look a bit further for reasons.

---

