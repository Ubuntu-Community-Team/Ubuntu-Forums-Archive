---
title: "Help getting the files"
date: 2008-02-22
forum: General Help
---

### Post by JeanLau on 2008-02-22
I need help badly!!! I wake up early in the morning to print my term paper (I need to pass it later) but I can't login to windows. Before it can show the logging screen a BSOD show up. I tried booting up in safe mode but no use. I can only bootup in ubuntu.** Another problem is since window is not properly shutdown, the SDA1 won't show up in Ubuntu gutsy. Are there anyway i can retrieve those files? (I only have 1 hdd)  **

The only reason i boot up in windows is because my printer epson 91 won't print in ubuntu. 

**It will be a big help I need those term paper to gradaute** :(.

---

### Post by bodhi.zazen on 2008-02-22
Well, if you have your Windows disk, lets just try to repair windows.

Try this :

In Windows XP, you can permanently uninstall GRUB as follows:

[list=number][*]Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console.
[*]Select your Windows XP installation from the list and enter the administrator password.
[*]At the input prompt, enter the command "FIXMBR" and confirm the query with "y".
[*]The MBR will be rewritten and GRUB will be uninstalled.
[*]Press "exit" to reboot the computer.[/list]

Later we can try to fix GRUB, like this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

