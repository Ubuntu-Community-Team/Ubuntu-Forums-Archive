---
title: "Command line question about directory"
date: 2015-01-24
forum: General Help
---

### Post by michael-piziak on 2015-01-24
I'm confused about how the name of my computer (which is michael) shows up in terminal.

For example, when I go to my Game Roms director (using cd 'Game Roms'), I then look at the directory I'm in using pwd command.

The result is that I get:

/home/michael/Game Roms

I'm a bit confused at why the name of my computer (michael) show's up 2nd after home directory.  It would seem logical to me that it should show up as:  /michael/home/Game Roms

?

Screenshot below.

---

### Post by Impavidus on 2015-01-24
The prompt says:```
**[COLOR=#ff00ff]michael[/COLOR]@[COLOR=#ff0000]micheal-HP-Compaq-dc5800-Small-Form-Factor[/COLOR]:[COLOR=#0080ff]~/Game Roms[/COLOR]$**
```This shows your **[COLOR=#ff00ff]user name[/COLOR]**, your **[color=#ff0000]computer's name[/color]** and finally your **[COLOR=#0080ff]current directory[/COLOR]**. Your user name is part of your current directory, as that is your home directory. The name of your home directory is **/home/username**, which can be shortened to **~**.

---

### Post by michael-piziak on 2015-01-24
I'm more puzzled by:  [COLOR=#000000]/home/michael/Game Roms

Why is it directory then username then directory I'm in.  Seems like the username wouldn't be in the middle.[/COLOR]

---

### Post by deadflowr on 2015-01-24
micheal is a directory within the home directory, and Games roms is within the micheal directory.
/home is a system directory which houses/holds the users home directory(ies).
If you have more than one user they would also get a directory within the home directory.

If that makes sense

---

### Post by Dennis N on 2015-01-24
It's because your home directory is **/home/michael**, not **/home**. All user's home directories are one level under /home

**/home** is owned by root.
**/home/michael** is owned by you

---

### Post by michael-piziak on 2015-01-24
Thanks.  
Marking this as solved.

---

