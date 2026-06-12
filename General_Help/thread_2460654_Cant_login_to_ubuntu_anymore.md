---
title: "Cant login to ubuntu anymore"
date: 2021-04-15
forum: General Help
---

### Post by mccoo8884 on 2021-04-15
When I start my PC I get to the purple welcome screen. I select my user and fill in the password (yes it is correct). Screen freezes, goes black for a second and then it goes back to the login screen.

Havent done anything weird before. What is going on.

---

### Post by TheFu on 2021-04-15
There are a number of different causes for the "login-loop" as this is called.
Change to a different TTY (press cntl-alt-F1), login on the console, then run:
```
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall
```
In theory, that will get your system fully patched and install any proprietary drivers - GPU, firmware, network.  That's the theory.
If stuff gets installed, reboot.  That will automatically bring up the GUI tty - which is on cntl-alt-F7 or it was last time I checked.

There are a number of TTYs. Just try F1-F9 and hit the <enter> key a few times until the login: prompt is displayed.
This is also handy when the GUI locks up, but everything else is fine.  Switch to a different console, login and kill the program using the most CPU/RAM.  Then switch back to the GUI console (C-A-F7?) and see if it is working again.  Shouldn't even need to login again unless the session manager or Xorg or Wayland were the issue.

Anyway, this has a 30% chance of fixing it, especially for nvidia GPUs. That's my guess, nothing scientific. Worth a shot and having an updated system is always good.

---

### Post by Impavidus on 2021-04-16
Another possibility is that the permissions on your home directory on some files in it are messed up. When your GUI session cannot write to the files it needs, it may crash at once, sending you back to the login screen. On the console you can make sure all files and directories in your home directory are owned by you.

---

### Post by ActionParsnip on 2021-04-16
Also make sure you have free space on all file systems

---

### Post by ajgreeny on 2021-04-16
Can you get to a tty command line using Ctrl+Alt+F3 at the login screen and login there?

If that is successful it rather points to the hidden ***.Xauthority*** file having incorrect permissions or ownership.
It must be owned by you, and you should have read/write permission but all others should have none.
Check it from the tty with command ***ls -la .Xauthority*** which should show ***-rw-------***

---

