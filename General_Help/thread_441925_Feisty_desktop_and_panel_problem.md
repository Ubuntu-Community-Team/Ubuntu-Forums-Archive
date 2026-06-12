---
title: "Feisty desktop and panel problem"
date: 2007-05-13
forum: General Help
---

### Post by fable on 2007-05-13
I installed Feisty a couple of weeks ago and everything was working fine.  Today I used Synpatic to install Firestarter.  After I installed and configured Firestarter, I wanted to auto start Firestarter every time I turn on the computer.  So I went into System -> Preference -> Session and tried to add a new start-up session by adding the following and then did a save current session:
```
sudo firestarter --start-hidden
```

After I did the above, I have the following problems:

- When I start any application, e.g. Firefox, the application will always open from the top left of the screen, right over the panel.  In other words, the panel will be hidden behind the application.

- I also noticed that Firestarter does not start every time I turn on the computer.  I checked the list of start-up sessions and Firestarter is not there.

The computer still works fine with all applications.  It is just very inconvenient to have the top and bottom panels hidden behind the application.

Anyone knows why I have this problem and how can I fix it?

:confused:

------------------Update:  This problem is solved -----------------------------------------

This problem is solved by deleting the gnome session file in ~/.gnome2/session.

---

### Post by fable on 2007-05-13
Right now all applications starts from the upper left corner of the screen.  The application also open right over the top and bottom panels making them not accessible.  I tried to locate the configuration file that specify the location of the window when an application starts but no luck.  I thought if I can find the configuration file I might fix this problem.

Anyone know which and where is the configuration file that tells an application the location to open on the screen?  Is the file in the /etc directory?  

:confused:

---

### Post by fable on 2007-05-13
Just an update.  I found out that this is reported as a bug is gnome-panel, bug #109760.

Logging in Failsafe GNOME mode do not have this problem.  Logging in as normal mode will have the problem.  The problem is still not fixed.

---

### Post by zvacet on 2007-05-13
If you use desktop version of Ubuntu just uninstall Firestarter.You don´t need it because you have firewll installed by default (iptables) and Firestarter is GUI for them.in desktop version you have all ports closed so you don´t have to worry.

---

### Post by fable on 2007-05-13
Thanks for the information.  I already uninstalled Firestarter but the panel problem is still there.  When I open an application the top and bottom panel will hid behind the application window.  I don't know how to fix this panel problem but it makes Feisty not practical to use.

---

### Post by fable on 2007-05-14
I found a fix to my problem.
I found out that the session file is in the hidden folder ~/.gnome2.
To fix this problem, simply go to terminal mode and delete the corrupted session file as follows:
```
sudo rm ~/.gnome2/session
```
After you deleted the file, simply reboot the computer and the top/bottom panels will be back to normal.
Everything on Feisty is working fine again on my computer.

:)

---

### Post by Ubris on 2007-05-19
FYI, this solved [a similar problem I had]("http://ubuntuforums.org/showthread.php?t=408054") (so thanks very much), and possibly will fix other kinds of desktop corruption. I have documented a [slightly more cautious variation]("http://ubuntuforums.org/showthread.php?t=408054#post2677538") on yours, which worked for me. Hope it helps.

---

