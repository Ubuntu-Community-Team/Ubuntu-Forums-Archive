---
title: "what are names for shells and terminals?"
date: 2019-11-13
forum: General Help
---

### Post by Skaperen on 2019-11-13
i am working on a program that scans upward through process ancestry.  i'd like to form a list of all possible names i might see interactive shells running under along with typical arguments, if any.  i'd like to do the same for the terminal process.

i am using "[COLOR=#0000cd][FONT=courier new]**ps -ef**[/FONT][/COLOR]" to get a list of processes, parents, and command lines.  should i read from [COLOR=#0000cd][FONT=courier new]**/proc**[/FONT][/COLOR] instead?

i am getting which workspaces that some processes are running in.  i use "[COLOR=#0000cd][FONT=courier new]**wmctrl -lp**[/FONT][/COLOR]" to get this info.  are there times i should use something else?

the project is a Python script to reveal what workspace number a script is running in since this is not automatically in an environment variable (i will be having my nearly 1000 line [COLOR=#0000cd][FONT=courier new]**.bashrc**[/FONT][/COLOR] file add it).

---

### Post by SeijiSensei on 2019-11-13
I'm not entirely sure what you're asking, but every shell I know of has "sh" in its name, like csh, bash, dash, zsh, etc.

---

### Post by TheFu on 2019-11-13
/etc/shells has the list of installed, valid, shells which can be used for logins.
That doesn't prevent a user from creating a script, compiling a binary, running it and considering it as a shell.

---

### Post by Skaperen on 2019-11-14
it looks like /etc/shells will be useful.  i can just read that and look for those.  i'll make up a "standard" and also read ~/.config/shells if it exists.  as for terminal names i tried looking for names with "terminal" but it failed on a friends Kubuntu system.  so maybe i need to look for just "term".  in most cases the terminal will be the parent of the shell.  but it would still be nice to know the program names of all the terminals.

---

### Post by TheFu on 2019-11-14
~/.config/shells isn't used.  The admin controls which shells a system can use, not end-users. The "shells" manpage is useful reading.

---

### Post by SeijiSensei on 2019-11-14
The name of the terminal application on Kubuntu is [Konsole]("https://kde.org/applications/system/org.kde.konsole"). This is one of the original KDE apps where everything began with a "K."

---

### Post by Skaperen on 2019-11-14
> **TheFu said:**
> ~/.config/shells isn't used.  The admin controls which shells a system can use, not end-users. The "shells" manpage is useful reading.

that's for login shells.  a user can execute another shell in its place.  maybe they would start recording private user shells there if programs that need to know are already looking there.  it's not used, yet.  something has to be first.

---

### Post by Skaperen on 2019-11-14
> **SeijiSensei said:**
> The name of the terminal application on Kubuntu is [Konsole]("https://kde.org/applications/system/org.kde.konsole"). This is one of the original KDE apps where everything began with a "K."

i added a check for "onsole" in my code that tries to figure out what workspace it is in: [http://ipal.net/python/whichws.py](http://ipal.net/python/whichws.py)

---

