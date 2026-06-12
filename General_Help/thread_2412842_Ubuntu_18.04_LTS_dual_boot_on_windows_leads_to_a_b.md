---
title: "Ubuntu 18.04 LTS dual boot on windows leads to a black screen after boot up"
date: 2019-02-18
forum: General Help
---

### Post by flipperacd on 2019-02-18
After choosing Ubuntu 18.04 LTS from the grub menu, it leads to a black screen, and my main monitor shuts off.
I found the 'nomodeset' fix, but for some reason i can not find a line that starts with 'linux' or has 'quiet splash' while editing grub.
if it helps, i have a Raedon RX 590.

---

### Post by yancek on 2019-02-18
When Ubuntu is highlighted on the Grub boot menu screen you should hit the 'e' key on your keyboard and see the entire menuentry for Ubuntu.  Use the down arrow key to get to the line beginning with linux and the right arrow key to move to the right to enter nomodeset.  If you don't see this, what do you see?

---

