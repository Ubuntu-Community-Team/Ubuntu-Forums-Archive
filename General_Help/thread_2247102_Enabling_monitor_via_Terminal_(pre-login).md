---
title: "Enabling monitor via Terminal (pre-login)"
date: 2014-10-05
forum: General Help
---

### Post by avro2 on 2014-10-05
Hitting one road block after another. It's getting a little tiresome. Anywho, I seem to have disabled my monitor in the System Settings! I'm trying to understand how to follow/solve the problem from this thread:

[http://askubuntu.com/questions/405645/how-to-enable-monitor-from-terminal](http://askubuntu.com/questions/405645/how-to-enable-monitor-from-terminal)

But I'm not following how the procedure is done. Is the thread above valid? Is there another of altering the monitor settings through guest?

Edit: all "xrandr" and "xset" commands don't seem to work in the terminal at the login screen (ctrl-alt-F1).

Edit #2: During the meantime of this problem, I just set a new user account. Still, any help will be much appreciated!

Edit #3: I got it! All I had to do was reinstall the ubuntu-desktop.  Afterwards I rebooted via terminal and logged in just fine. Here are the  steps I took:

            1. Login into my account with the monitor settings disabled
            2. Once in (and with black screen), I hit ctrl-alt-F* to open the terminal screen
            3. Logged in, set my user pathway to the wanted account
            4. Typed, "sudo apt-get install ubuntu-desktop"
            5. Went into root to reboot

Cheers!

---

