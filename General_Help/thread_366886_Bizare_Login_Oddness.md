---
title: "Bizare Login Oddness"
date: 2007-02-21
forum: General Help
---

### Post by omega13a on 2007-02-21
It all started yesterday when I went to go turn on my computer.  The normal Edgy Ubuntu login screen showed up and I entered my username and password.  So far so good.  About what seemed like two to three minutes went by and that thing that GNOME start up thingy or what ever it is called still hadn't showed up.  All there was was that tan colored background.  Then suddenly my screen went black for a sec and a blue login screen showed up that had a yellow flower in the bottom right hand corner.  I entered my username and password again and I got into my computer.  Everything else seemed fine.  Since then, this has happen every time I shut down my computer and boot it up.  I have no clue what is wrong.  Any help would be greatly appreciated. Thanks in advance.

---

### Post by chggr on 2007-02-21
Try this:

1) Click on System -> Administration -> Login Window
2) You will see a list of themes you can use to customize the login window
3) The default theme is "Human". Select it and press close.

If you logout and logon again, the problem should be solved...

---

### Post by omega13a on 2007-02-21
> **chggr said:**
> Try this:

1) Click on System -> Administration -> Login Window


It wouldn't open so I decided to run the program from the command line so I can see what was going on.  I got this:

omega13a@omega13a:~$ sudo gdmsetup
Password:
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

Something is fishy here...  Any ideas on how to fix that?

---

