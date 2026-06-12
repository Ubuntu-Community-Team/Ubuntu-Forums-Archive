---
title: "Failed to log in"
date: 2017-10-05
forum: General Help
---

### Post by assma on 2017-10-05
Hello Dear all,
Before yesterday I have run the update software in my ubuntu 14.04 but I turn off my computer before the updates finished. Now I faild to log in my session, it is a kind of a loop session. I tried many solutions in the net but they didn't solve my problem. I can even get connected via my ethernet interface. 
Could you please help me? 
Thank you very much

---

### Post by Impavidus on 2017-10-05
Can you boot into recovery mode? That should present you with a menu. Try the option to fix broken packages.

---

### Post by ajgreeny on 2017-10-05
You could also try **Ctrl+Alt+F1** when you get to the login page to take you to a command-line.
Login there with your username and password (password will not show on screen, not even as *s).

If you manage to login there, run the command ```
sudo apt-get update && sudo apt-get upgrade
```  and it may solve this for you, though that will depend on just how far the process had got last time.

Report back here with any error messages you get.

---

### Post by assma on 2017-10-05
Thank you all, for your replies
I tried the recovery mode but it did not solve the problem
I tried also the "apt-get update" but there are some packages that failed to be installed

---

### Post by assma on 2017-10-05
I solved the problem by following:
1 - I installed the grup to be able to recovery my system
2 - I enabled the network
3 - Try to recover the broken packages
4 - Ctrl + Alt + F1 
5 - I set the file /etc/apt/sources.list to the defaults dependencies
6 - update and upgrade
7 - In the end I went again to the recovery mode and recover broken packages, this time it does work 
8 - Restart the system twice

---

