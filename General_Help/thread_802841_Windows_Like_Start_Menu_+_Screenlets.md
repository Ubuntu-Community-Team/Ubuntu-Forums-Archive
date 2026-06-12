---
title: "Windows Like Start Menu + Screenlets"
date: 2008-05-21
forum: General Help
---

### Post by Krimson13 on 2008-05-21
I was playing around with Screenlets. I really like the main menu option. It's organize in a way I like. It's a lot like the Windows start menu. How would I be able to set up Ubuntu 8.04 to act like this app in the upper panel?

[INDENT]Also, I having an issue with Screenlets. Whenever I start up the program it asks...
> There is no existing autostart directory for your user account yet. Do you want me to automatically create it for you?
After hitting Yes...
> Automatic creation failed. Please manually create the directory:
/home/james/.config/autostart/


Well, I thought if I went to the directory and do...
```
Sudo mkdir autostart
```
it would fix my problem. The problem is that it's not hidden or there period. However the terminal claims it exists. Any advice?[/INDENT]

---

### Post by EXCiD3 on 2008-05-22
Does putting in the full path create the directory?
```
sudo mkdir /home/james/.config/autostart
```

Being a screenlet as it is, im not sure that you will be able to add it to the upper panel. You could try using KDE instead of Gnome because it is much more like this screenlet than Gnome is. 

Also, what icon set do you use?

---

### Post by Forlong on 2008-05-22
**Do not run random commands with sudo!**

That is exactly what your problem is. You are locking yourself out of your home directory.


Open a terminal and run ```
sudo chown -R $USER:$USER $HOME
``` (just copy & paste the command as it is), this will make sure you are the owner of all the files in your home directory.
Afterwards run ```
chmod -R u+rwx $HOME
``` to make sure, you have the proper rights to those files.


Then let Screenlets create the folder for you.

---

