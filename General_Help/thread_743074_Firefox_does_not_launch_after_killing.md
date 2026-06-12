---
title: "Firefox does not launch after killing"
date: 2008-04-02
forum: General Help
---

### Post by dohnp5a1 on 2008-04-02
After trying to launch Firefox, I received the message it has been launched yet, although nowhere the program was visible. In desperation I used the ability Kill process in Administration and killed both firefox and firefox-bin. Thereafter I was not capable to launch Firefox. It always is starting several seconds in the lower panel but after it dissapears. I tried to delete .mozilla in my personal directory, I reinstalled the package firefox, nevertheless it did not help.

After  "sudo dpkg-reconfigure firefox" it writes "Please restart any running Firefoxes, or you will experience problems." although Ubuntu is just restarted and no Firefox is started.

After the command "firefox":

pad@pad-laptop:~$ firefox
pad@pad-laptop:~$

(although the program has not started)

Also "sudo apt-get --purge --reinstall install firefox firefox-gnome-support" does not help,

neither post "sudo killall -9 firefox" and "sudo killall -9 firefox-bin".

The file "lock" in ~/.mozilla/firefox/8chars.default/ is always created anew post killing firefox and firefox-bin and trying to launch firefox, also in -safe-mode. Without previous killing the two processes it is not created.

The command  "sudo dpkg-reconfigure firefox" used in "recovery mode" produces the answer "Please restart any running Firefoxes, or you will experience problems." too.

---

### Post by cdenley on 2008-04-02
Did you try deleting .mozilla, then restart to ensure any firefox-related processes are no longer running?

---

### Post by dohnp5a1 on 2008-04-02
Yes, I did.

---

### Post by cdenley on 2008-04-02
If you deleted your profile and restarted your computer, I'm not sure what the problem could be. Files can continue to be accessed after they are deleted, so you can check with this command.
```

lsof -n|grep ~/.mozilla

```

---

### Post by dohnp5a1 on 2008-04-02
pad@pad-laptop:~$ lsof -n|grep ~/.mozilla
pad@pad-laptop:~$ 

Without change, I still cannot launch the application.

---

