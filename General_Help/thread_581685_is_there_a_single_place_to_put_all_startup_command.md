---
title: "is there a single place to put all startup commands and apps?"
date: 2007-10-19
forum: General Help
---

### Post by pixeldotz on 2007-10-19
i've been using ubuntu for about a year now and have ubuntu studio installed on my lappy and use it every day :).

my question is this, is there a single place where all startup commands can be entered and executed? preferably as root?

i notice when i search on this subject people mentino /etc/rc.local or startup programs menu or modules file or the fstab.

i was wondering if there was single place where ALL of this could be done instead of doing something in fstab then putting something else in rc.local and and such.

for instance. i usually manually mount my windows share using a command i have stored in my file of need-to-know-commands (i'm sure most of you have one of these).

i see people refer to using fstab for this. i can also use it as a startup command from the system menu/preferences menu.
i haven't tried it with rc.local though.

but i also have some chmod commands i have to execute on boot. so i guess my question is; can i put all these commands in one central location and have them execute when i login? and not have to open 4 different places to do that?
(fyi: i'm not bashing ubuntu and i'm not talking out of frustration, i just want to know if everything can be centralized? one of the things that dropped me into linux in the first place with the multitude of being able to do one task from many different angles)

---

### Post by dayvy on 2007-10-19
All those files are for different things. fstab is for mounting partitions, modules is for loading modules (drivers), rc.local is for executing scripts before login. If you click on "System" -> "Preferences" -> "Sessions" you'll see that you can add startup programs there. These will be loaded once you login to gnome.

Hope this clarifies a few things.

---

