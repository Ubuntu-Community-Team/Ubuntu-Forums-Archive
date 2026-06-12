---
title: "Properly-Working System: Fixing Underlying Problems"
date: 2023-06-06
forum: General Help
---

### Post by wyattwhiteeagle on 2023-06-06
How can I get a list of all logs, journals, etc that is on my machine?

---

### Post by guiverc on 2023-06-07
I'm not sure what you're asking for, but 

- If I want a list of system messages, I usually use `dmesg`
- If I want to view systemd journal, I use `journalctl` (*this will go further back & not just current session*)
- If I want to view *deb* package logs, I'll `view /var/log/apt/history.log`
..
- If I wanted to view Xorg logs, I'd likely  `view /var/log/Xorg.0.log` etc
...

However what logs that exist will depend on what package(s) you actually have installed.  I usually start at `dmesg`, though if exploring issues on prior session/boots I'll want to use systemd journal, then package logs.. and usually don't go beyond that before I have a pretty good idea of where I need to look (ie. *the Xorg log & others I rarely have need to touch as I find they only come into the picture after I've made changes; meaning I usually already know where to look*).

There are many logs found in /var/log.

---

### Post by wyattwhiteeagle on 2023-06-07
> **guiverc said:**
> I'm not sure what you're asking for, but 

- If I want a list of system messages, I usually use `dmesg`
- If I want to view systemd journal, I use `journalctl` (*this will go further back & not just current session*)
- If I want to view *deb* package logs, I'll `view /var/log/apt/history.log`
..
- If I wanted to view Xorg logs, I'd likely  `view /var/log/Xorg.0.log` etc
...

However what logs that exist will depend on what package(s) you actually have installed.  I usually start at `dmesg`, though if exploring issues on prior session/boots I'll want to use systemd journal, then package logs.. and usually don't go beyond that before I have a pretty good idea of where I need to look (ie. *the Xorg log & others I rarely have need to touch as I find they only come into the picture after I've made changes; meaning I usually already know where to look*).

There are many logs found in /var/log.
Thank you
I asked for all journals, logs, etc.

Package logs...
Are there more than deb's, such as ppa packages?
If ppa's can be deb's, or vice versa, please explain the differences.
I avoid snap's.

---

### Post by guiverc on 2023-06-07
Log files are generally in /var/log/

SystemD has *binary* log files, which is one of the things people didn't like about it when I replaced sysvinit, thus using commands like `journactl` are just easier.

All *deb* package logs are in /var/log/apt/history.log regardless of where they were from, ie. be they Ubuntu repositories, you manually downloaded it (`wget` etc) & installed it (`dpkg -i`) from terminal, OR from 3rd party sources such as PPA (*personal package archives*), so where from doesn't matter; all *deb* package installs will go there.

Non *deb* packages installs will not be there, ie. /var/log/apt/ won't contain details about *appimage, flatpak, snap**, or compiled from source* where some of those will require you to explore your own logs (.bash_history or the appropriate place for whatever shell you use etc)

For all logs - the best answer I can give you is /var/log/   as there is no single source for where they are, as our OS is built from many components/projects that use different standards (BSD, Linux, GNU, GNOME, Qt/KDE, etc) and thus the *standard* for any particular tool varies on where that tool came from.

---

### Post by wyattwhiteeagle on 2023-06-07
How do I view the bash history?
How do I determine what shell I use?

---

### Post by guiverc on 2023-06-07
> **wyattwhiteeagle said:**
> How do I view the bash history?
How do I determine what shell I use?

You can use the `history` command to view bash history, eg. 

```

guiverc@d7050-next:~$   history
...
   80  23/05/26 15:43:29 rmadison linux-image-generic-hwe-22.04-edge
   81  23/05/27 13:20:20 sudo snap refresh; sudo apt update; sudo apt full-upgrade ; sudo apt autoclean; sudo apt autoremove; neofetch

```

To view it in file format, I'd use
```

guiverc@d7050-next:~$   view .bash_history 
...
#1685079809
rmadison linux-image-generic-hwe-22.04-edge
#1685157620
sudo snap refresh; sudo apt update; sudo apt full-upgrade ; sudo apt autoclean; sudo apt autoremove; neofetch

```

where I've edited the output to show only example(s)...  Note also:  date/time of command isn't shown by default, but I've added that, also most commands I execute aren't recorded there intentionally as if you notice the `view .bash_history` command I did paste you may notice a number of SPACES before the actual `view` command; which causes that command I used as example for copy/paste here won't be entered in my history.

Three times per day I re-run that `snap refresh.. apt full-upgrade` type command; where I use UP arrow to find it, then press <HOME>< >< >& enter so it's not repeated endlessly in history.

To view what SHELL I'm using, I could use

```

guiverc@d7050-next:~$   echo $SHELL
/bin/bash
guiverc@d7050-next:~$   stat ~/.bash_history 
  File: /home/guiverc/.bash_history
  Size: 4855            Blocks: 16         IO Block: 4096   regular file
Device: 8,6     Inode: 1708985     Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/ guiverc)   Gid: ( 1000/ guiverc)
Access: 2023-06-07 16:48:59.998894836 +1000
Modify: 2023-05-27 13:22:28.487104614 +1000
Change: 2023-05-27 13:22:28.487104614 +1000
 Birth: 2023-04-05 23:45:23.538810765 +1000

```

ie. I'm using BASH thus command history is stored in .bash_history which is located in ~, or $HOME, ie. `/home/guiverc/.bash_history` for me.  A quick look at dates will show my last 'saved' command was 27-May, yet I've run more than >40 commands today (all no doubt were spaced out thus not saved... I intentionally only don't space out for commands I'll want to find again OR may used a command that will  change something usually (*thus I want the date/time & record*).

---

### Post by ajgreeny on 2023-06-07
Your own use of the terminal, ie, cli commands using bash (mostly) will be found in the hidden text file in your home named **.bash_history**.

Use ctrl+H to view hidden folders and files in whichever file manager you normally use and you will see all the commands used recently if you open that file; how many you see depends on the **history** setting in another hidden file in your home named **.bashrc**

---

### Post by wyattwhiteeagle on 2023-06-08
I already limited the size of the rotating logs in /etc/logrotate.d

How would I limit the growing size of other logs not under /etc/logrotate.d?
How would I filter in all the relevant info to underlying problems?

What do I do with this...
What is ACPI and FADT/Gpe0Block and tbfadt?
> ```
tac /var/log/dmesg
```


[    0.021007] kernel: ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/64 (20210730/tbfadt-564)

---

### Post by wyattwhiteeagle on 2023-07-16
> **guiverc said:**
> You can use the `history` command to view bash history, eg.


```

guiverc@d7050-next:~$   history
...
   80  23/05/26 15:43:29 rmadison linux-image-generic-hwe-22.04-edge
   81  23/05/27 13:20:20 sudo snap refresh; sudo apt update; sudo apt full-upgrade ; sudo apt autoclean; sudo apt autoremove; neofetch

```

Where in .bashrc do I add the \d or \D prompt to show date/time of command without specifying any GNU Emacs style escape sequences, a second set of backslash escapes which will delete things?

Each LTS version comes out every two years.
Is there a way to have it show "YYYY/MM/DD 24hr-time" for my timezone?

Is the below done as a cron job?
> **guiverc said:**
> Three times per day I re-run that `snap refresh.. apt full-upgrade` type command; where I use UP arrow to find it, then press <HOME>< >< >& enter so it's not repeated endlessly in history.

---

### Post by Holger_Gehrke on 2023-07-16
[ACPI]("https://wiki.osdev.org/ACPI") 
[FADT]("https://wiki.osdev.org/FADT")
The warning is about a bug in your Firmware which produces a different size of value in the FADT than expected. Nothing you can do about it except possibly update the Firmware of your main board. Unless of course it's very new board that correctly implements a new standard which the kernel doesn't implement yet, then you have to wait for a new kernel that fixes the problem.

Re:history
normally there are no timestamps in history. But if you set the variable "HISTTIMEFORMAT" to a time format as used by strftime(), history will insert timestamps in the history (that's the lines with a '#' followed by a number, the seconds since epoch) and print those times in that format when listing the history.
BTW you can do an incremental search in the command history with '^R'. That's a lot quicker than searching manually ...

Holger

---

### Post by wyattwhiteeagle on 2023-07-16
> **Holger_Gehrke said:**
> [ACPI]("https://wiki.osdev.org/ACPI") 
[FADT]("https://wiki.osdev.org/FADT")
The warning is about a bug in your Firmware which produces a different size of value in the FADT than expected. Nothing you can do about it except possibly update the Firmware of your main board. Unless of course it's very new board that correctly implements a new standard which the kernel doesn't implement yet, then you have to wait for a new kernel that fixes the problem.

Re:history
normally there are no timestamps in history. But if you set the variable "HISTTIMEFORMAT" to a time format as used by strftime(), history will insert timestamps in the history (that's the lines with a '#' followed by a number, the seconds since epoch) and print those times in that format when listing the history.
BTW you can do an incremental search in the command history with '^R'. That's a lot quicker than searching manually ...

Holger
Thanks

My machine is from the Windows Vista era.
Chances are it's a bug that I can't do anything about just as you mentioned.

Re: History,
In the bash manpage it talks about the "day month and date" just as quiverc shows in his post by using the "\d" prompt in .bashrc,
not the format which you mention.

I'm not exactly sure where the /d prompt goes in the specified lines.
The manpage doesn't mention where it should go in the lines.

From the bash manpage...
Note that it says nothing about where these prompts should go.
The .bashrc doesn't show it either.
Only the manpage mentions it.
but doesn't give examples or anything like that.
 > 

PROMPTING
       When executing interactively, bash displays the primary prompt PS1 when it is ready
       to  read  a  command, and the secondary prompt PS2 when it needs more input to com&#8208;
       plete a command.  Bash displays PS0 after it reads a command but  before  executing
       it.   Bash  displays PS4 as described above before tracing each command when the -x
       option is enabled.  Bash allows these prompt strings to be customized by  inserting
       a number of backslash-escaped special characters that are decoded as follows:
              \a     an ASCII bell character (07)
              \d     the date in "Weekday Month Date" format (e.g., "Tue May 26")
\D{format}
                     the  format  is passed to strftime(3) and the result is inserted into
                     the prompt string; an empty format results in a locale-specific  time
                     representation.  The braces are required


---

### Post by Holger_Gehrke on 2023-07-17
That's something completely different. It would give you a date / time stamp as part of the prompt (PS1). Search for 'HISTTIMEFORMAT' in the bash manual page. It's in the section 'PARAMETERS' in the  'Shell Variables' sub-section. I use '%F %T' which gives me an ISO-Date followed by 24 hour time. In my ~/.bashrc I have
```

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000
# timestamps in history
HISTTIMEFORMAT='%F %T '

```

Holger

---

### Post by wyattwhiteeagle on 2023-07-17
> **Holger_Gehrke said:**
> That's something completely different. It would give you a date / time stamp as part of the prompt (PS1). Search for 'HISTTIMEFORMAT' in the bash manual page. It's in the section 'PARAMETERS' in the  'Shell Variables' sub-section. I use '%F %T' which gives me an ISO-Date followed by 24 hour time. In my ~/.bashrc I have
```

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000
# timestamps in history
HISTTIMEFORMAT='%F %T '

```

Holger
Thank you

This will help to know if it's something I'm doing that is contributing to the underlying problems in my machine.
Or at least which commands I run when not using spaces before the command.
Also when those commands are ran.

---

### Post by wyattwhiteeagle on 2023-08-26
When looking to resolve things, let's say an error, goin on with my machine, do I begin working on the oldest error or the newest one?

Trying to minimize the chances of getting such message's as "Cannot perform the operation. Code xyz." or something like that.
I believe, don't quote me on this, that is a message to mean, "The error which correspond's to the given code needs to be corrected before attempting to execute this operation."

---

