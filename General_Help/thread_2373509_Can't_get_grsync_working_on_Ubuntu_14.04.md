---
title: "Can't get grsync working on Ubuntu 14.04"
date: 2017-10-06
forum: General Help
---

### Post by 5circles on 2017-10-06
I can't see the buttons on grsync to allow me to execute.  I have not used Ubuntu from the desktop for quite a while - which is why I'm still running 14.04 until I can get the hierarchy copied to a NAS.   But I've tried quite a few things, including:

[LIST]Uninstalling and reinstall grsync[/LIST]
[LIST]Uninstalling the stock version that is in the 14.04 repository (1.2.4) and installing 1.2.7[/LIST]
[LIST]Running under gksu.  No difference except that the session buttons sort of work[/LIST]
[LIST]Changing to Gnome from Ubuntu default[/LIST]


Nothing seems to work, but I'm pretty sure it worked before.

When I'm running as a regular user, if I start grsync from the terminal and exit, I see "Can't open config file! Maybe this is the first run?"  If I run from the terminal using gksu I don't get the message.

I'd really like to get grsync to work, but I've spent so much time on this that it would probably be better for me to use rsync directly.

Any ideas would be most appreciated.
Thanks
Mike

---

### Post by ajgreeny on 2017-10-07
In your home there should be a hidden folder named **.grsync** and in that a file named **grsync.ini**.

Check that you have that and that both the folder and the file have read write permissions for you as user.
Using it as root is not necessary and also not a very good idea in normal circumstances.

---

### Post by speartip on 2017-10-07
I'm using 16.04. But on my version of Grsync, the execute button is the cog in the top right of the screen. There's 4 buttons  + x i then the execute cog.
If they're greyed out then check the .grsync hidden folder in your home folder to check it's not locked by wrong permissions, or delete that folder for a clean instance of grsync.

---

### Post by 5circles on 2017-10-07
The basic problem was the .grsync directory and files - permissions / ownership.  I don't know why the complete removal and reinstall didn't set the hierarchy up correctly.  I changed ownership to .grsync/* and now the screen makes more sense - I could see sessions properly, and if invoked from the terminal it exited properly.

The buttons still confused me, but perhaps the screenshots were from much older versions.  Plus, either hovers weren't working (perhaps because of permissions) or it was just me not recently using Ubuntu.  I can't tell right now because it's running.  The file menu has the simulate and execute options, and the cog (which I can hover over while it's running) is instead of execute.


Many thanks

---

### Post by ajgreeny on 2017-10-08
A complete removal of a package, ie, purging it, does not remove any configurations in the user's home, only the config in the root filesystem, eg, /etc or /use/lib.
This is an intentional behaviour,exactly as expected.

---

