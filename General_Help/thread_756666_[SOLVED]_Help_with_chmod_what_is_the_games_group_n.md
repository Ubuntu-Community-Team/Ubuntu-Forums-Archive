---
title: "[SOLVED] Help with chmod: what is the games group number?"
date: 2008-04-16
forum: General Help
---

### Post by end-user on 2008-04-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/94512](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/94512) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				What number group is games in Linux (or Ubuntu if each distro is different) for using chmod so I can give read/write access back to NetHack for its folder? And is that what I would want to do to fix this:

I recently switched from Kubuntu back to Ubuntu, and I wanted to keep all my scores, saves, bone files, etc. for NetHack, so I saved my old /var/games/nethack folder and replaced the new NetHack folder from the same location with it.

When I tried to run Nethack, I get an error message about Nethack not being able to write to there. I tried changing the permissions to include read/write access for games and clicking "apply permissions to enclosed files" using gksudo Nautilus but apparently there is currently a [bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/94512") with [Nautilus]("http://bugzilla.gnome.org/show_bug.cgi?id=352895") and the changes don't get applied. These bugs say that only ownership can't be changed this way - but I'm not able to change permissions either.

How can I achieve this from the console - and for future reference, is this the only way I could have saved all of my scores, etc?

EDIT: I might have a few things wrong - maybe Nautilus can't change the group permissions recursively either, but it can with "Others". Is "Others" in the permissions tab of Nautilus the same as what chmod affects, or would chmod also affect groups?

---

### Post by darksizzle on 2008-04-16
Ummm I don't know much about games on Ubuntu or what you're trying to do too much but if you're having permissions issues and you're wanting to chmod something recursively you can try the following things:

The games gid is 60, you can see this when you look in /etc/group 'e.g. in terminal type less /etc/group' you'll notice something like games:x:60:, your gid is the 3rd column.

You don't really need the gid though 'cause you can chown the directory like so:
chown -R 'root:games' /path/to/directory

the -R flag specifies you want to change the ownership to all the files below the parent directory, I chose root:games because that's what I saw when I looked into /var/games

If you want a quick and dirty way to see if it's a permissions issue you can to a quick check with something like:
chmod -R a+rw /path/to/directory

The specifies that you would like to give user:group:others all read and write access so you have no worries about who owns what.  You should figure out the correct group and set the permissions accordingly.

Hope that get's you somewhere.

---

### Post by Gen2ly on 2008-04-16
I've done this before, restore some backup files after re-installing the system.  The thing is the system assigns the game group # arbitrarily meaning it just grabs a number everytime the compter is setup.   Run "ls -l" from the terminal and it will tell the group number if a the games group number doesn't match it.  To fix the nethack files the chgrp command can be used:

```
chgrp -R games nethack
```

This will change recursively all files and folders in the nethack folder.

---

### Post by end-user on 2008-04-16
Thank you both. I went ahead and used the chgrp command - that did it! I guess I should have started looking for the chgrp command - but all of the permissions stuff I've dealt with so far in the console was chown or chmod,  and always mentioned these gids, so I assumed all I needed to know the numerical code.

Nice to learn a couple new commands when they are relevant and likely to stick in my memory, like "less".

Thanks again!

---

