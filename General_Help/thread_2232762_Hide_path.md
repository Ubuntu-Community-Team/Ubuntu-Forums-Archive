---
title: "Hide path"
date: 2014-07-04
forum: General Help
---

### Post by kakashi_12 on 2014-07-04
Is there a way a path can be hidden in a window? Just below the Title bar, it shows the url of where you are in the pc/filesystem. Is there a way to have this path hidden?

---

### Post by TheFu on 2014-07-04
Usually, yes.
It is just a CLI startup setting for the terminal. Whether that is possible will depend on the program used.  I use xterms and the man page for it says 
>   -T string
               This  option  specifies  the  title for xterm's windows.  It is
               equivalent to -title.
So ... I'd try that with whatever program you are trying. If it doesn't work, RTFM. ;)

I hope that makes sense.

---

### Post by sudodus on 2014-07-04
Or do you mean the [COLOR=#0000ff]path[/COLOR] shown at the prompt?

```
[COLOR=#008000]sudodus@work-horse[/COLOR] [COLOR=#0000ff]/media/multimed-2[/COLOR] $
```

Usually the prompt is set in your bash configuration file ***~/.bashrc***

```
PS1='...'
```

and you can get the simple prompt **$** with the following command (temporarily in a terminal window or persistent if you edit [I][B]~/.bashrc

[/B][/I]```
PS1='\$ '
```

From ```
man bash
```

```
       PS1    The  value  of  this parameter is expanded (see PROMPTING below) and used as the primary
              prompt string.  The default value is ``\s-\v\$ ''.
       PS2    The value of this parameter is expanded as with PS1 and used  as  the  secondary  prompt
              string.  The default is ``> ''.
       PS3    The  value  of  this  parameter  is used as the prompt for the select command (see SHELL
              GRAMMAR above).
       PS4    The value of this parameter is expanded as with PS1 and the value is printed before each
              command  bash  displays during an execution trace.  The first character of PS4 is repli&#8208;
              cated multiple times, as necessary, to indicate multiple  levels  of  indirection.   The
              default is ``+ ''.

```

```
PROMPTING
       When  executing  interactively, bash displays the primary prompt PS1 when it is ready to read a
       command, and the secondary prompt PS2 when it needs more input to  complete  a  command.   Bash
       allows these prompt strings to be customized by inserting a number of backslash-escaped special
       characters that are decoded as follows:
              \a     an ASCII bell character (07)
              \d     the date in "Weekday Month Date" format (e.g., "Tue May 26")
              \D{format}
                     the format is passed to strftime(3) and the result is inserted  into  the  prompt
                     string;  an  empty  format results in a locale-specific time representation.  The
                     braces are required
              \e     an ASCII escape character (033)
              \h     the hostname up to the first `.'
              \H     the hostname
              \j     the number of jobs currently managed by the shell
              \l     the basename of the shell's terminal device name
              \n     newline
              \r     carriage return
              \s     the name of the shell, the basename of $0 (the portion following the final slash)
              \t     the current time in 24-hour HH:MM:SS format
              \T     the current time in 12-hour HH:MM:SS format
              \@     the current time in 12-hour am/pm format
              \A     the current time in 24-hour HH:MM format
              \u     the username of the current user
              \v     the version of bash (e.g., 2.00)
              \V     the release of bash, version + patch level (e.g., 2.00.0)
              \w     the current working directory, with $HOME abbreviated  with  a  tilde  (uses  the
                     value of the PROMPT_DIRTRIM variable)
              \W     the  basename  of  the  current  working directory, with $HOME abbreviated with a
                     tilde
              \!     the history number of this command
              \#     the command number of this command
              \$     if the effective UID is 0, a #, otherwise a $
              \nnn   the character corresponding to the octal number nnn
              \\     a backslash
              \[     begin a sequence of non-printing characters, which could be used to embed a  ter&#8208;
                     minal control sequence into the prompt
              \]     end a sequence of non-printing characters

       The  command  number and the history number are usually different: the history number of a com&#8208;
       mand is its position in the history list, which may include commands restored from the  history
       file  (see HISTORY below), while the command number is the position in the sequence of commands
       executed during the current shell session.  After the string is decoded,  it  is  expanded  via
       parameter  expansion, command substitution, arithmetic expansion, and quote removal, subject to
       the value of the promptvars shell option (see the description of the shopt command under  SHELL
       BUILTIN COMMANDS below).

```

---

### Post by Bucky Ball on 2014-07-04
Hidden in a window belonging to what app? A file manager address bar? Terminal? :-k

---

### Post by kakashi_12 on 2014-07-04
Window Manager. Not terminal.

---

### Post by kakashi_12 on 2014-07-04
Nevermind. I found a way to hide the true directory. By using bind instead of a link (shortcut).
Can someone explain to me the difference between Links and Binding, before I close this thread please? Thanks.

---

### Post by TheFu on 2014-07-04
> **kakashi_12 said:**
> Window Manager. Not terminal.

IME, WMs don't have windows ... they manage them for other apps.  So ... which app - SPECIFICALLY - is the path being displayed in the titlebar?

It would help us help you if we knew which release, WM, DE was being used too.

---

### Post by TheFu on 2014-07-04
Which sort of linking?  symbolic or hard?  Binds are more like hardlinks ... but not the same.  

Asking for explanations is easy. Being complete, accurate, understandable is hard.

Wikipedia does a good job on symlink and hardlink explanations. [https://en.wikipedia.org/wiki/Symbolic_link](https://en.wikipedia.org/wiki/Symbolic_link) thankfully.

---

