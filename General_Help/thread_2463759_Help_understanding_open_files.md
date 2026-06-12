---
title: "Help understanding open files"
date: 2021-06-17
forum: General Help
---

### Post by ugxtgiqgapkgyonwqx on 2021-06-17
I frequently encounter issues where I'm not able to launch apps.  Even something as simple as Ctrl + Alt + T doesn't open the terminal.  I found a post on SO (didn't save the link) that didn't actually solve the issue but provided a workaround:

```
$ lsof -U +c 15 | cut -f1 -d' ' | sort | uniq -c | sort -rn | head -3
lsof: WARNING: can't stat() tracefs file system /sys/kernel/debug/tracing
      Output information may be incomplete.
    370 chrome
    110 dbus-daemon
     79 slack
```

The first line of the man page for lsof tells me that the command "list[s] open files".  I have several applications open, so it doesn't surprise me that I have lots of files open.  And I'm pretty sure the OS has a limit to the number of open files at a time.

However, I'm pretty sure that chrome has a lot more than 370 files open:```
$ lsof | grep -i chrome | wc -l
57611
```

The simplest solution would be to stop using apps with so many open file handles, but alas I do not have that luxury on a work computer.  Usually if I kill slack I can launch apps again; then I can re-launch slack.

Not sure if it matters, but I'm on Ubuntu 18.04.5 LTS

Questions:
How can I find the *real* list of apps with the most open files?  I understand the [FONT=courier new]+c 15[/FONT] switch but I don't understand what [FONT=courier new]-U[/FONT] does
Could I increase the max number of open files?  What would be the downsides of doing so?

---

### Post by Holger_Gehrke on 2021-06-18
The -U limits lsof to list Unix Domain Sockets - file-like things that  are used for interprocess communication. Leave that option out to get a  list showing the number of all open files.

You can find out the number of files you can open with 'cat /proc/sys/fs/file-max'. /proc/sys/fs/file-max is not a real file, it's an internal variable made accessible as if it was a file. You can change the maximum number of open files with 'sysctl -w fs.file-max=newValue' (substitute the obvious) for the current session or permanently by adding a line 'fs.file-max=newValue' to /etc/sysctl.conf. On my system I've got a limit of ~ 700000, never changed the default and never ran into the kind of trouble you have. AFAIK all desktop flavours of Ubuntu have file limits in that order of magnitude, only servers have less (they don't have a GUI and mostly aren't used interactively, so they don't need as many open files).

Holger

---

