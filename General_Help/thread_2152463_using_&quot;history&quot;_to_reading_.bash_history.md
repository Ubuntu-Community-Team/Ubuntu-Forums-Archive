---
title: "using &quot;history&quot; to reading .bash_history from another system"
date: 2013-06-07
forum: General Help
---

### Post by George Heine on 2013-06-07
I have a copy of  .bash_history file from computer Y, and want to read it on computer X.
It is easy to open a text editor, but would like to use the "history" command on X to interpret the timestamps from Y.
(Both computers have HISTTIMEFORMAT set to the same value).

Thanks for any help.

---

### Post by tgalati4 on 2013-06-07
If I understand the manpage correctly:

HISTTIMEFORMAT
              If this variable is set and not null, its value is used as a format string for strftime(3) to print the time  stamp  associated  with  each
              history  entry  displayed by the history builtin.  If this variable is set, time stamps are written to the history file [I]so they may be pre&#8208;
              served across shell sessions[/I].  This uses the history comment character to distinguish timestamps from other history lines.


I interpret this to mean accross several shell sessions on the same system.  Because *history* is a bash built-in command, you might have to examine the source code to understand how it works and how a particular history file is associated with a specific session ID.  When you simply copy the .bash_history file to another computer, there is no association with bash and that history file.

My guess is that this is either a Use Case that was not programmed into bash or a security precaution.  It would be trivial to change or insert a history file onto an infected system and then have an active shell interpret it.

Perhaps explain what you are trying to do.  There may be a better way to remotely execute a series of commands from one system to another:  

```
ssh username@machinename scriptofcommandsthatIwanttoexecute.sh
```

---

### Post by George Heine on 2013-06-08
> Perhaps explain what you are trying to do.  There may be a better way to  remotely execute a series of commands from one system to another:  


Okay, here's the scenario.  System Y has suddenly stopped booting. 

 I was able to get on with a rescue disk, look at and copy .bash_history to an external disk drive.
Was hoping that looking at the history file would give me a clue as to what command or commands might have corrupted the boot loader.
I can look at the commands, but knowning the date and time might give me some additional clues.

I am not interested in executing the commands on system X, only reading them.

Thanks for any help you might be able to provide.

---

### Post by steeldriver on 2013-06-08
Did you try invoking a bash subshell with the HISTFILE variable i.e.

```
$ HISTFILE=your_other_file bash
```

e.g. if I make a 'new' history file by taking the top 10 lines of my current history

```
$ head ~/.bash_history > ~/bash_history_old
```

then
```

$ HISTFILE=bash_history_old bash
$ 
$ history
    1  cat << EOF
    2  The list is:
    3  ${var// /\\n}
    4  EOF
    5  cat << EOF
    6  The list is:
    7  ${var// /$}
    8  EOF
    9  history

```

In any case, I think it's just a plain readable text file so you can use any old editor (or 'less') ro read it

---

