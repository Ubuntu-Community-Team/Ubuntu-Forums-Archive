---
title: "where is the executable file supposed to be located?"
date: 2024-10-15
forum: General Help
---

### Post by Skaperen on 2024-10-15
*Ubuntu* has merged [FONT=courier new]/bin[/FONT] with [FONT=courier new]/usr/bin[/FONT] and [FONT=courier new]/sbin[/FONT] with [FONT=courier new]/usr/sbin[/FONT].  what i would like to know is, for some given command name, which directory its executable file would be in, had the merge not taken place.  when i make a script that has commands that need be written as full path, i want to know which path to be used.  what i used to do was check which it was in, such as by doing:
```

ls {/usr,}/bin/foo

```
now it lists the file in both locations.  either will work fine on this version (and flavor) of *Ubuntu*, but what if the script is run somewhere else, such as an older *Ubuntu*, some other distro, or *BSD*?  how can i get the correct path if my *Xubuntu* system has these paths merged?

---

### Post by philhughes on 2024-10-16
You can use "which" or "command -v". See the following for a discussion:

[https://www.shellcheck.net/wiki/SC2230](https://www.shellcheck.net/wiki/SC2230)

---

### Post by The Cog on 2024-10-16
In terms of knowing where a file *should* go, you need to query the package database. e.g.:
```

dpkg-query -S /bin/foo && FOO=/bin/foo
dpkg-query -S /usr/bin/foo && FOO=/usr/bin/foo
$FOO
```
If you just want to reliably run it in your scripts, maybe:
```
$(ls {/usr,}/bin/foo | head -1)
```
If you just want to re-use the found location:
```
FOO=$(ls {/usr,}/bin/foo | head -1)
$FOO

```

---

### Post by grahammechanical on 2024-10-16
In Files>Other Locations>Ubuntu there is a bin folder that is just a link to usr/bin. The icon has an arrow pointing away from the top right corner. Other folders are likewise links to the actual location of the folder.

In my install of 24.04.1 there are these folders bin.usr-is-merged; lib.usr-is-merged & sbin.usr-is-merged. The three folders are empty.

Regards

---

### Post by Skaperen on 2024-10-16
> **philhughes said:**
> You can use "which" or "command -v". See the following for a discussion:

[https://www.shellcheck.net/wiki/SC2230](https://www.shellcheck.net/wiki/SC2230)

neither works.  "which" just searches PATH and could find a like named command in an earlier directory.  if i have PATH='/usr/bin:/bin' then "which" will report "/usr/bin/..." in all cases where everything is in both.

"command -v" produces the same thing.  it tells me "/usr/bin/mkdir" because "/usr/bin" is ahead of "/bin" in my PATH variable.  its documentation (around line 3000 of "man bash") is rather vague and ambiguous.  but it is definitely giving me incorrect results in test cases.

my question is more about what is the traditional or intended location of certain commands.  critical sysadmin commands are in "/bin" so that repairs can be made to bring the whole system up.  examples include "ls" and "mkdir".

my fallback plan is to install an older system in a VM and record what it has in "/bin".  then make a script that mimics "which" and looks in that list and if it's'n there and exists in "/bin" (regardless where else it exists) then result it as being in "/bin".  i have a script, now, named "wh" that outputs all locations of a command (i have many directories with some override scripts).

---

### Post by Skaperen on 2024-10-16
> **The Cog said:**
> In terms of knowing where a file *should* go, you need to query the package database. e.g.:
```

dpkg-query -S /bin/foo && FOO=/bin/foo
dpkg-query -S /usr/bin/foo && FOO=/usr/bin/foo
$FOO
```
If you just want to reliably run it in your scripts, maybe:
```
$(ls {/usr,}/bin/foo | head -1)
```
If you just want to re-use the found location:
```
FOO=$(ls {/usr,}/bin/foo | head -1)
$FOO

```

that seems to be getting correct answers.  i'd like to know where it knows this.

---

### Post by Skaperen on 2024-10-16
> **grahammechanical said:**
> In Files>Other Locations>Ubuntu there is a bin folder that is just a link to usr/bin. The icon has an arrow pointing away from the top right corner. Other folders are likewise links to the actual location of the folder.

In my install of 24.04.1 there are these folders bin.usr-is-merged; lib.usr-is-merged & sbin.usr-is-merged. The three folders are empty.

Regards

i don' have "Files" so i cannot see "Files>Other Locations >Ubuntu".  that could be because i am still on 20.04.

---

### Post by The Cog on 2024-10-17
> that seems to be getting correct answers. i'd like to know where it knows this.
[FONT=Courier New][COLOR="#0000FF"]dpkg-query -S /bin/foo[/COLOR][/FONT] asks dpkg what package provides /bin/foo. It either succeeds and prints the package name (in which case the following [FONT=Courier New][COLOR="#0000FF"]&& FOO=/bin/foo runs[/COLOR][/FONT]) or it fails because it "should be" somewhere else, and FOO is not set.

[FONT=Courier New][COLOR="#0000FF"]ls {/usr,}/bin/foo | head -1[/COLOR][/FONT] tries to list foo in both locations. It might list more than one if dirs are symlinked. [FONT=Courier New][COLOR="#0000FF"]head -1[/COLOR][/FONT] takes only the first item listed. This approach will use the first location listed whether or not it's just a symlink.

In both cases, putting the command inside $(...) runs the command and then uses its captured output as a command-line input.

---

### Post by davetheoldcoder on 2024-10-17
> **Skaperen said:**
> i don' have "Files" so i cannot see "Files>Other Locations >Ubuntu".  that could be because i am still on 20.04.

"Files" is the "friendly name" for Nautilus, the default file manager in 24.04. It may have a different "friendly name" in 20.04. And "Other Locations" might also be different in 20.04, but should be there in some form.

---

### Post by Skaperen on 2024-10-18
> **The Cog said:**
> [FONT=Courier New][COLOR=#0000FF]dpkg-query -S /bin/foo[/COLOR][/FONT] asks dpkg what package provides /bin/foo. It wither succeeds and prints the package name (in which case the following [FONT=Courier New][COLOR=#0000FF]&& FOO=/bin/foo runs[/COLOR][/FONT]) or it fails because it "should be" somewhere else, and FOO is not set.

[FONT=Courier New][COLOR=#0000FF]ls {/usr,}/bin/foo | head -1[/COLOR][/FONT] tries to list foo in both locations. It might list more than one if dirs are symlinked. [FONT=Courier New][COLOR=#0000FF]head -1[/COLOR][/FONT] takes only the first item listed. This approach will use the first location listed whether or not it's just a symlink.

In both cases, putting the command inside $(...) runs the command and then uses its captured output as a command-line input.

i ran it outside of $(...) and just looked at what it output.  it sounds like this should work, but the output was the command without the path.

i'm not trying to make a script to answer this.  i'm just wanting to know this about a new command i'm putting in a script that might be run without a PATH environment set right.  i had a command name in mind when started the thread but i knew i would just have to ask again for the next, so i decide to ask how to find out.  i vaguely recall some web site that had such a list but in my old age i am bad at remembering URLs and other like details.  i've learned to keep notes, now.  but i didn't have one for this.

---

### Post by Skaperen on 2024-10-18
i'm not much of a GUI user.  i use command line for most things.  i am an old coder, too.  i do use GUI to run things like firefox and mplayer and such.  i'm learning to start scripts from desktop icons but i don't know how to make my script be a GUI app, yet.  so i was probably looking in the wrong place.  the name "Nautilus" in not known to me, but i am on Xubuntu 20.04 so it might not even be here.  i don't even know the names of most GUI things i do use.  my file manger is "bash" and "ls".  i have a bunch of terminal windows running, usually 6 per userid, usually full screen each.

---

### Post by Holger_Gehrke on 2024-10-18
'nautilus' is the graphical file manager in Gnome. 'Thunar' would be the equivalent in Xubuntu. 

The solution by 'The Cog' relies on the (Debian-) package having the right stored path for the file. So if you're executing your script on a machine running a distribution with another package manager it will fail.

The directory merge is actually meant to make scripting more reliable across distributions since there always were programs that resided in /bin in one distro and in /usr/bin on others; with the files all in /usr/bin and /bin a symlink to /usr/bin scripts which use either path will work. It doesn't help with programs that reside in /sbin on one distro and in /bin on another ...

Starting scripts from the GUI isn't all that complicated, all that's necessary is a *.desktop file either in the ~/Desktop directory or in one of the directories from which the menus of the GUI are generated (/usr/share/applications/, /usr/local/share/applications/,~/.local/applications). What's much more interesting is writing scripts which actually have a GUI. 'zenity' is useful for that, it's like 'dialog' but GTK-based. There used to be a program named 'gtkdialog' which allowed you to write shell scripts with a full GUI, but it's been dead for a decade.

Holger

---

### Post by Skaperen on 2024-10-19
> **Holger_Gehrke said:**
> 
The directory merge is actually meant to make scripting more reliable across distributions since there always were programs that resided in /bin in one distro and in /usr/bin on others; with the files all in /usr/bin and /bin a symlink to /usr/bin scripts which use either path will work. It doesn't help with programs that reside in /sbin on one distro and in /bin on another ...


if the location can vary over the span of distros, that makes a script using full paths to run a command unreliable.  that is a risk i need to consider.  perhaps i need to set check if PATH is set and set it if not.

first thought: (we always expect bash, like most shells, to be in /bin)
```

#!/bin/bash
[[ -n "$PATH" ]] || export PATH='/usr/bin:/bin'
...

```
if bash is not available... i could use /bin/sh if what i want to do does not need bash (most things could be coded for /bin/sh but bash is easier to code for.  so the above test could need the test command if i want my script to span that wide.

> **Holger_Gehrke said:**
> 
Starting scripts from the GUI isn't all that complicated, all that's necessary is a *.desktop file either in the ~/Desktop directory or in one of the directories from which the menus of the GUI are generated (/usr/share/applications/, /usr/local/share/applications/,~/.local/applications). What's much more interesting is writing scripts which actually have a GUI. 'zenity' is useful for that, it's like 'dialog' but GTK-based. There used to be a program named 'gtkdialog' which allowed you to write shell scripts with a full GUI, but it's been dead for a decade.

Holger

i think my ~/Desktop directory is getting full.  my desktop screen has over 100 icons, now.

for a script that does it's own GUI, i'm inclined to use Python, which has its own tools for that.  Python is usually in /usr/bin but sometimes in other places.

---

