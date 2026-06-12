---
title: "Uninstalling?"
date: 2007-02-01
forum: General Help
---

### Post by tenkabuto on 2007-02-01
Hi, I am trying to run a gaming program in Ubuntu using Wine. I installed it using Wine, but now cannot find it in the Program Files. :confused: Now when I try to reinstall, I get an error. How can I uninstall the program from Windows, while in Linux?

---

### Post by pseudonym on 2007-02-02
This might sound obvious, but try looking in the other directories on your 'fake c drive'. Not every Windows game installs into 'Program Files'.

If the game has an uninstall.exe (or similar) you can try running it with 'wine uninstall.exe' but often you need to delete the game directory to 'uninstall' it (though this method will leave some settings behind in the 'fake registry', which is no big deal really). 

If it's the only windows app you've got in wine it's even better to delete your whole ~/.wine directory and generate a new one with the 'winecfg' command.

---

