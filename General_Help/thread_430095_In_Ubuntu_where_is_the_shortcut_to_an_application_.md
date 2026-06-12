---
title: "In Ubuntu where is the shortcut to an application installed by Automatix or Synpatic?"
date: 2007-05-01
forum: General Help
---

### Post by fable on 2007-05-01
I am still new to Ubuntu and Linux.  I found Automatix2 and Synpatic very useful for installing new applications.  However, sometimes when I install an application, I don't know where it is installed.  It does not show up in the menu bars on top.  

For example, I installed Debian Menu using Automatix2.  After Automatix2 finished the installation, I could not find an icon in the Application menu above nor the binary file in /usr.  

Can someone tell me where Ubuntu installed the application?  Also, how can I add a shortcut to the application in the panel on top?

---

### Post by Ziggy72 on 2007-05-01
Like you, I had a problem getting the Debian Menu to show in the Applications Menu. I suggest you look at [http://ubuntuforums.org/showthread.php?t=416134](http://ubuntuforums.org/showthread.php?t=416134) to see how I was able to resolve the problem. Good luck...

---

### Post by fragos on 2007-05-01
I can't speak for Automatrix but most Synaptic installed packages place an entry in the main menu.  If it doesn't you can use the menu editor to add an entry.  You will need to determine the installed name of the executable to add it.  Synaptic seems to place executibles in the the $PATH so you don't need to provide a path with the program name..  You can verify a program name in a terminal window with the command "which {name}".

---

### Post by fable on 2007-05-02
Thanks for pointing me to the solution.  I did the following as suggested:

```
sudo dpkg-reconfigure menu
sudo dpkg-reconfigure menu-xdg
```

Then I reboot the computer.  After reboot, the Debian Menu appears in the "Application" pulldown menu.

:)

---

### Post by R_U_Q_R_U on 2007-08-31
> **fable said:**
> Thanks for pointing me to the solution.  I did the following as suggested:

```
sudo dpkg-reconfigure menu
sudo dpkg-reconfigure menu-xdg
```Then I reboot the computer.  After reboot, the Debian Menu appears in the "Application" pulldown menu.

:)


I have tried this with no success.

---

