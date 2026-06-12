---
title: "No crontab in root..Now What?"
date: 2022-02-14
forum: General Help
---

### Post by wyattwhiteeagle on 2022-02-14
In Ubuntu 18.04, root had a crontab.

Now in 20.04.3, there are no crontab's in /root.

Where did it go?

Do I just keep the custom rdiff backup script in a convenient location such as a flashdrive and run it daily in terminal under sudo command?

---

### Post by Tadaen_Sylvermane on 2022-02-14
There never were any crontabs in /root. They are kept in /var/spool/cron/crontabs. If you had scripts in /root though then you can put them there as long as the path in crontab knows where they are. You can put them wherever you want really.

---

### Post by wyattwhiteeagle on 2022-02-14
> **Tadaen_Sylvermane said:**
> ...crontabs...are kept in /var/spool/cron/crontabs...


On my system, that directory is empty.


Do I need to create, copy or move one to the crontabs location?


Baobab detects that crontabs contains 1 item, but crontabs properties say's it contains nothing.


There are only 3 crontab files.


Their locations are...
> 1. /etc
2. /usr/bin
3. /usr/share/bash-completion/completions

---

### Post by SeijiSensei on 2022-02-14
If you use the crontab command to create the files, they will be stored in /var/spool/cron/crontabs. Each user has a separate file using the creator's username. (You need to be root to look into this directory.)  If you create your scripts manually, you can place them in a variety of areas.  /etc/cron.daily is a good place to put scripts that need to be run each day.

You can also modify the system-wide /etc/crontab as root, but be aware that directives in this file require that you specify the user in the file.  Use "less /etc/crontab" to see more details.

---

### Post by ActionParsnip on 2022-02-14
Users have no crontab by default. You can make one by running
```

crontab -e

```

Then setting one up

---

### Post by SeijiSensei on 2022-02-14
Also you can control the editor used by crontab if you set the EDITOR environment variable.

```
EDITOR=nano; crontab -e
```

---

### Post by schragge on 2022-02-14
It's either
```
EDITOR=nano crontab -e
```
or
```
export EDITOR=nano; crontab -e
```

---

### Post by coley9225 on 2022-02-15
Hello. I am  far from an expert,  but it's my understanding that 'crontab -e' will allow you to editor your USER crontab. If I understand your goal, try 'sudo crontab -e'. That will give you a root crontab, and no need to use sudo in your commands. Hope this helps.

---

### Post by ActionParsnip on 2022-02-15
> **coley9225 said:**
> Hello. I am  far from an expert,  but it's my understanding that 'crontab -e' will allow you to editor your USER crontab. If I understand your goal, try 'sudo crontab -e'. That will give you a root crontab, and no need to use sudo in your commands. Hope this helps.

^ this

---

### Post by wyattwhiteeagle on 2022-02-15
Does it need to be nano or do I have a choice...such as...

instead of
```
[COLOR=#000000][FONT=&quot]EDITOR=nano; crontab -e[/FONT][/COLOR]
```

Can I use
```
[COLOR=#000000][FONT=&quot]EDITOR=gedit; crontab -e[/FONT][/COLOR]
```

---

### Post by ActionParsnip on 2022-02-15
Try it....

---

### Post by wyattwhiteeagle on 2022-02-15
> **ActionParsnip said:**
> Try it....

Nah...not yet.

For now I think I will "[COLOR=#000000]/etc/cron.daily is a good place to put scripts that need to be run each day."[/COLOR]

---

### Post by SeijiSensei on 2022-02-15
> **wyattwhiteeagle said:**
> Does it need to be nano or do I have a choice
It can be any terminal-based editor.  I use jed myself. If you don't specify an editor, "crontab -e" will prompt for one based on what appears on the system. I tried using a GUI editor, kate in my case, but that didn't work.

I usually put items that require root privileges into /etc/crontab rather than using "sudo crontab -e".

---

### Post by #&amp;thj^% on 2022-02-15
> **SeijiSensei said:**
> 
I usually put items that require root privileges into /etc/crontab rather than using "sudo crontab -e".

+1 I as well.

---

### Post by kevdog on 2022-02-16
I dont think you can use gedit (never tried) but I think the editor has to be command line based, like nano, emacs, vi,vim, etc.  

I thought since Ubuntu 20.04 is systemd based, the recommended way to set up "cron style" commands was to actually use systemd timers associated with a systemd unit file.  I'm aware there are multiple ways to "skin the cat" however I thought this was the recommended way.  I've converted most (but not all) of my crontab commands into systemd unit files (timer files, unit files) and have been pleased.  Everything logs to journalctl and its pretty easy to query the status and also get email or other notifiers if the command didn't complete successfully.

---

### Post by TheFu on 2022-02-22
There are 2 different formats for crontabs depending on the location on disk.
/etc/crontab is the system crontab. It adds more columns to control which userid a task gets run using.

crontab -e creates per-userid crontabs in /var/spool/....  The userid is known, so not necessary.

To help prevent mistakes in per-userid crontabls, I add this comment block to the top of each:
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  /full/path/command --arg1 --arg2 file1 file2  > /tmp/log.file  2>&1
```

Hope this helps someone.  The example command is very useful. Learn about shell redirection to understand all the stuff at the end.  The github page "The Art of the Command Line" goes into it. Very useful.
Also, cron expects to send the output at completion to the userid or root using an installed MTA (postfix/sendmail/exim), so those really are necessary to see the output. There are all sorts of well-known techniques to only get error emails, not "all is fine" emails from cron. Subtle, but important, techniques.
I would strongly discourage ever sending cron created emails to public email accounts on email systems you don't own. There is often sensitive data in those emails. Best not to give it to gmail, for example.

---

