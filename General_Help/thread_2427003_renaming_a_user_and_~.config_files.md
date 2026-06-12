---
title: "renaming a user and ~/.config files"
date: 2019-09-16
forum: General Help
---

### Post by Skaperen on 2019-09-16
i have noticed many files in [COLOR=#0000cd][FONT=courier new]**~/.config**[/FONT][/COLOR] have the actual user name or the full path of the user's home directory.  if i want to rename to user and rename the home directory to match (and do [COLOR=#0000cd][FONT=courier new]**chown -hR**[/FONT][/COLOR] if a userid number change was also involved) i presume i should also [COLOR=#0000cd][FONT=courier new]**sed -i**[/FONT][/COLOR] all those file to reflect the change (while no processes are running for this user).  but i have run across a difficulty.  file [COLOR=#0000cd][FONT=courier new]**~/.config/dbus/user**[/FONT][/COLOR] is in a binary format.  if the name involves a different length, that could throw off lengths and offsets, corrupting the file.  any ideas or suggestions?

---

### Post by dragonfly41 on 2019-09-17
[Creating an alias to user name]("https://superuser.com/questions/367608/is-it-possible-to-alias-a-username-on-linux") was the first thought that popped into my head. But I have not tried it.

---

### Post by Skaperen on 2019-09-18
i want to also be able to create a new user (of a different name, of course) that is an identical copy of a user that stays, as well as moving a user to a different system where a name change is neede.

---

### Post by TheFu on 2019-09-18
I'd guess the best you can do is make a new userid, then copy the HOME directory over from the other one and hope for the best.  Unix programmers would know to base all their preferences off $HOME for the userid or some override environment variable.  The non-Unix programmers would make all sorts of dumb assumptions and fail to handle the HOME change issue.  When you come across specific programs, open a bug with each project team.

---

### Post by SeijiSensei on 2019-09-18
If you want to create a template for a new user, put the files you want to use in /etc/skel.  Then when you create a new user, those files will be imported into that user's directory. Usually /etc/skel just contains a bunch of dot files like .bashrc, but you can put other things in there as well.

---

### Post by Skaperen on 2019-09-18
> **TheFu said:**
> I'd guess the best you can do is make a new userid, then copy the HOME directory over from the other one and hope for the best.  Unix programmers would know to base all their preferences off $HOME for the userid or some override environment variable.  The non-Unix programmers would make all sorts of dumb assumptions and fail to handle the HOME change issue.  When you come across specific programs, open a bug with each project team.

the problem is so many of today's application developers don't do this right.  that and they put these wrong paths in files like [COLOR=#0000cd]**[FONT=courier new]~/.config/dconf/user[/FONT]**[/COLOR] where it is very non-trivial to fix them because that file has a binary format.  they should be using relative or referential paths and non-binary files (like XML or JSON).

i was making a copy of a user to become a "template" user to make more copies from, in the future.  what i did, for now, is leave ~/.config/dconf/user out a hope for the best.  i think that is better than leaving in references to paths in the wrong home directory.  other settings files are text files, so, i did change those with sed.  the goal is to have the graphical settings be the same so i don't have to do a manual setup for each such user i create.

if you (any reader of this post) are a developer of an application that stores persistent data or settings in the user's home directory, please store the home directory path part as "~/" instead of the full path name.  all major programming languages have tools to convert this back.  in Python, see the [COLOR=#0000cd]**[FONT=courier new]pathlib[/FONT]**[/COLOR] module.

---

