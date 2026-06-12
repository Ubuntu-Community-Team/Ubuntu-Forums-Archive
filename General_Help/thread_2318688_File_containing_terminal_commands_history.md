---
title: "File containing terminal commands history"
date: 2016-03-28
forum: General Help
---

### Post by lakeshore2985 on 2016-03-28
What is the file containing all user's terminal commands ever used? I know it stores the entries somewhere in /bin I guess? Where was it?

Thanks!

---

### Post by coldraven on 2016-03-28
Have a look in your home folder for a hidden file called .bash_history

---

### Post by QDR06VV9 on 2016-03-28
Bash maintains the list of commands internally in memory while it's running. They are written into .bash_history on exit:

When an interactive shell exits, the last $HISTSIZE lines are copied from the history list to the file named by $HISTFILE

If you want to force the command history to be written out, you can use the history -a command, which will:

    Append the new history lines (history lines entered since the beginning of the current Bash session) to the history file.

**There is also a -w option:**

    Write out the current history to the history file.

which may suit you more depending on exactly how you use your history.

If you want to make sure that they're always written immediately, you can put that command into your PROMPT_COMMAND variable:

[B]export PROMPT_COMMAND='history -a'

[/B]But you can see all that has been entered by simply putting **"history"** in the terminal.(With out the quotes"

[B]EDIT: If you want that printed to a text file on your desktop:

[/B]```
history >Desktop/bashhistory
```

Hope this was helpful.

---

### Post by vasa1 on 2016-03-28
And also look at *~/.bashrc* because you can modify aspects of *~/.bash_history*.

For example:```

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

```

---

### Post by lakeshore2985 on 2016-04-07
This sure was helpful!

Thanks!

---

