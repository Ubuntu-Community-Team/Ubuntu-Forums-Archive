---
title: "[SOLVED] The linux &amp;quot;at&amp;quot; command. A working example?"
date: 2007-08-28
forum: General Help
---

### Post by chrismyers on 2007-08-28
Hi Guys,

I'm trying to use the at command to schedule a wget, but I'm having trouble with the syntax.

I feel utterly stupid because I'm reading the man page, but whatever I do the darn thing wont work for me.

Can anyone give me a working example so I can translate it into something I can use?

Cheers.

---

### Post by apetresc on 2007-08-28
Yeah, sure :) I use 'at' every night to set an alarm for the following morning. Here's exactly what I type:```
root@petrescu:~ # at 5:30
warning: commands will be executed using /bin/sh
at> mpg123 /home/adrian/alarm.mp3
at> <EOT>
job 3 at 2007-08-29 05:30
root@petrescu:~ # atq
3       2007-08-29 05:30 a root

```
The "atq" checks to make sure my task is in the queue.

Good luck!

**EDIT:** Sorry, fixed wrong tag usage. The code should appear correctly now.

---

### Post by Wolki on 2007-08-28
> **AdrianP said:**
> ```
root@petrescu:~ # at 5:30
warning: commands will be executed using /bin/sh
at> mpg123 /home/adrian/alarm.mp3
at> <EOT>
job 3 at 2007-08-29 05:30

```


You can also pipe commands into the at for easier reuse:

```

echo "mpg123 /home/adrian/alarm.mp3" | at 5:30

```

And as a bonus tip for everyone who wants to have nice GUI integration for something like this. save the following somewhere:

> #!/bin/bash
WAKEUPTIME=$(zenity --entry --title="Alarm Clock" --text="Please enter when you want to wake up." --entry-text="5:30")
echo "mpg123 /home/adrian/alarm.mp3" | at ${WAKEUPTIME} 

Make it executable, then add a launcher to it on your panel or desktop. Don't forget to edit the command to suit your needs.

---

### Post by spupy on 2007-08-28
A quick addition: If you use "at" like post #2 (no piping), you must press Control-D to stop entering commands.

---

### Post by pmg on 2007-08-28
As another little tip, to help test your **at** command you can use a time of "**now**" so you don't have to wait. For example:```
echo *some_command* | at now
```and it'll run the command in the **at** environment right away.

---

### Post by chrismyers on 2007-08-30
Thanks guys, much appreciated.

I was trying to put the whole command in on one line. I didn't realize that all I had to do was type:

at midnight [enter]

wget [http://cdimage.ubuntu.com/releases/gutsy/tribe-5/gutsy-desktop-i386.iso](http://cdimage.ubuntu.com/releases/gutsy/tribe-5/gutsy-desktop-i386.iso) [ctrl-d]

Everythings easy when you know how isnt it?

:lolflag:

---

