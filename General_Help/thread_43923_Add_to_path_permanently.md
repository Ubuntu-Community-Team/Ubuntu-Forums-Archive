---
title: "Add to path permanently?"
date: 2005-06-23
forum: General Help
---

### Post by speedsix on 2005-06-23
How do I add directories to the path permanently, I've tried adding to bash_rc but this hasn't seemed to have worked?

Many thanks

---

### Post by desdinova on 2005-06-23
[QUOTE=speedsix]How do I add directories to the path permanently, I've tried adding to bash_rc but this hasn't seemed to have worked?

Many thanks[/QUOTE]

Did you log out and then log back in?

What exactly did you add to your .bashrc?

---

### Post by wylfing on 2005-06-23
Adding lines to .bashrc or .bash_profile won't work, because no bash shells (login or otherwise) are launched at startup. If you're trying to modify $PATH for your own preference, I suggest putting a command into your Gnome session startup configuration. From the main menu, choose System > Preferences > Sessions. Click the Startup Programs tab. Click Add, and type (for example):
```
export PATH=~/bin:"${PATH}"
```to add your private 'bin' directory to your path. Replace '~/bin' with whatever you wanted to add to PATH. Then click OK.

Then log out and log in again. Open a terminal and type ```
echo $PATH
``` and see if it's what you wanted.

---

### Post by desdinova on 2005-06-23
[QUOTE=wylfing]Adding lines to .bashrc or .bash_profile won't work, because no bash shells (login or otherwise) are launched at startup. If you're trying to modify $PATH for your own preference, I suggest putting a command into your Gnome session startup configuration. From the main menu, choose System > Preferences > Sessions. Click the Startup Programs tab. Click Add, and type (for example):
```
export PATH=~/bin:"${PATH}"
```to add your private 'bin' directory to your path. Replace '~/bin' with whatever you wanted to add to PATH. Then click OK.

Then log out and log in again. Open a terminal and type ```
echo $PATH
``` and see if it's what you wanted.[/QUOTE]

But it will work for any terminal sessions launched after the additional lines are entered...

---

