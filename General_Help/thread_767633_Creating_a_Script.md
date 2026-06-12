---
title: "Creating a Script"
date: 2008-04-25
forum: General Help
---

### Post by bryder2162 on 2008-04-25
Hi!

Being a newbie to Linux, I've been exploring this new world for the last month or so.  I recently installed GUTSY on PS3.  One of the how-to topics mentions making a script for the system to revert control to the PS3 OS.  Here is what the person wrote:

Code:
#!/bin/bash

sudo -v
sudo boot-game-os
sudo shutdown now -r

He instructs you to save it where ever you want and give it any old file name.  Call me stupid...but nowhere in his little how-to does he mention HOW TO make a script.  So, how do I???  Do I need to save it with a special extension?

Thanks

---

### Post by mc4man on 2008-04-25
just create a new text file on desktop, name it whatever and paste your script in. Then from terminal ex.
```
doug@doug-desktop:~$ cd Desktop
doug@doug-desktop:~/Desktop$ chmod a+x whatever
```




it should turn into diamond shape - d. click, ect.

---

