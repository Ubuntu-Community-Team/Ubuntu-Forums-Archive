---
title: "Finding details about a running process"
date: 2016-08-26
forum: General Help
---

### Post by neif1983 on 2016-08-26
Is there a way to find out what command was used (or what file was triggered) on a running process?

For example, when I type the top command, I can see that the top running process is FFMPEG
Can I know what command triggered this process? OR which file (bash script, etc..)?

Please help.

---

### Post by TheFu on 2016-08-26
The parent processID for each command is listed in the process table. Use "ps" to see this.
A normal ps command to see everything is **ps -eaf**.  There are probably scripts/programs written to show parent PIDs and trace up and down the process table. I've just never used them.

Another way to see something like this is the **lsof** (list open files) cmd.  You'll need to experiment with the output to see the stuff you'd be interested in seeing. Every file opened by every process is listed and this is a huge security issue, so sudo will be necessary.

---

### Post by Habitual on 2016-08-26
in top, I usually had to press c to show the COMMAND in its entirety.
Other tools, other tricks.

---

### Post by dragonfly41 on 2016-08-26
(1) Launch System Monitor GUI (Applications > System Tools > System Monitor)

(2) In System Monitor open Processes tab

(3) For any running process (e.g. gedit) right click and select Properties

(4) Inspect property Command Line

---

### Post by steeldriver on 2016-08-26
You may find pstree useful, especially with the -s option

```

DESCRIPTION
       pstree shows running processes as a tree.  The tree is rooted at either
       pid  or  init  if  pid  is  omitted.   If a user name is specified, all
       process trees rooted at processes owned by that user are shown.
.
.
.
       -s     Show parent processes of the specified process.
.

```

---

### Post by neif1983 on 2016-08-26
That is brilliant! Thanks everyone for the help.
Never heard of lsof before, looks great... Now I need to narrow down the results...

---

### Post by Habitual on 2016-08-26
Glad to be of help.

---

