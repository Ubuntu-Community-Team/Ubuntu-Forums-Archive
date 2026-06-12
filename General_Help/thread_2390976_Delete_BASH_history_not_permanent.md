---
title: "Delete BASH history not permanent"
date: 2018-05-04
forum: General Help
---

### Post by strungoutfan78 on 2018-05-04
This is a strange one.  I've been doing some testing for a shell script that contains sensitive info.  To test, I've been entering the entire command string manually into the bash prompt.  I had just planned on removing the entries in BASH history that contain sensitive data, but every time I exit the terminal and reopen it the lines I just deleted have returned.

Why the heck are these deleted lines returning and how do I make this stop?  I need to get this info out of my history.

I'm using Terminator for my terminal emulator.

Thanks

---

### Post by Holger_Gehrke on 2018-05-04
In bash the command 'history' without any options will give you a list of all commands in history with line numbers. 'history -d linenumber' will delete the given line from history.Write the history to the history file with 'history -w' afterwards. To stop the shell from putting a command into history you can start the line with a space assuming the variable HISTCONTROL is set to either 'ignoreboth' (default on Ubuntu) or 'ignorespace'.

Holger

---

### Post by ajgreeny on 2018-05-04
You have completely lost me, I'm afraid; deleting text from the terminal does not remove that text from bash history if the command has already been run

In order to delete lines from your bash history you need to open the hidden **~/.bash_history** file with a text editor, GUI or command-line such as nano, delete the lines and then save the edited file, or you could no doubt do it with a sed command, but I do not know sed well enough to help you more.  I also do not know terminator so have no idea if that is pertinent to your problem

Are you definitely using bash and not some other shell?

---

### Post by QIII on 2018-05-04
Hello!

If you just want to nuke it all:

```
cat /dev/null > ~/.bash_history && history -c && exit
```

That will clear the .bash_history file, clear the history in memory (so that it won't just get added back to .bash_history) and take you out of the terminal.

Otherwise, remove lines from ~/.bash_history as above and run

```
history -c
``` to clean up what is in memory.

---

### Post by monkeybrain20122 on 2018-05-04
You have to delete the lines from the .bash_history text file.

---

### Post by The Cog on 2018-05-04
Or use **history -c **to clear the history in the shell's memory, then **history -w** to write the blank memory back to the history file. 
Remember, as long as you have a terminal open there are two copies of the history - one in memory and one on disk.

---

### Post by QIII on 2018-05-04
> **The Cog said:**
> Remember, as long as you have a terminal open there are two copies of the history - one in memory and one on disk.

Thanks for making that explicit!  Sigh.  It's the implicit stuff that you forget to tell folks -- which is why they sometimes get frustrated.

---

