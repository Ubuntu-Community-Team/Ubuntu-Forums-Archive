---
title: "at command does not work"
date: 2007-03-24
forum: General Help
---

### Post by otilesoj on 2007-03-24
at command does not work with programs like firefox, evolution, etc

It seems like it does not work with windows programs
with other programs it works
for example:

at now
shutdown -h now
WORKS

at now
firefox
DOES NOT WORK

Any ideas?
Thanks
Jose

---

### Post by jeffathehutt on 2007-03-24
I'm pretty sure the at command isn't working right because it doesn't know which display to use.  Instead of just using the command 'firefox', try using 'DISPLAY=:0 firefox' and see if it makes a difference.

---

### Post by SuSUntu on 2007-03-24
JeffaTheHutt was on the right track about the display  being the issue, but his example doesn't work (for me).

Basically, the 'at' command adopts all the environment variables at the time the command is issued except for:

TERM, DISPLAY and ``_''

> 

**Runtime Environment**

Note that the plain old Bourne shell is used for all commands run by at. (Also note: I had to type ctrl-d, the *nix EOF character to close the interactive at session. More on this in the section on the at command line. This is just one factor affecting the behavior of at scheduled commands. Here are some other facts to bear in mind. **The present working directory, environment variables (with three exceptions, see below), the current userid and the umask that were in effect when the at command was issued are retained and will be used when the commands are executed. The three environment variable exceptions are TERM, DISPLAY and ``_'' (which usually contains the last command executed in the shell).** The output of the commands is mailed to the user who issued the at command. If the at command is issued in an su shell (meaning, if you ``became'' another user), the output mail will be sent to the login user, but the programs will run under the su user.

Source = [http://www.linuxjournal.com/article/4087](http://www.linuxjournal.com/article/4087)
  


If you look at the 'at' job (script) created in '/var/spool/cron/atjobs' with a text editor, you will see all the environment info it collects; notably missing is the DISPLAY variable. If you were to copy the 'at' job file to your desktop and run it manually, it would launch the GUI application as you wanted. That's because launching in such a way, the DISPLAY variable is known.

However, to get it to launch via the 'at' daemon, you must specify which display like so:

```

$: at now
>export DISPLAY=:0.0
>firefox
>type CTRL+d keys

```

Anyway, that works for me.

---

### Post by jeffathehutt on 2007-03-24
Thanks for the clarification SuSUntu.  I can't say I have ever used the at command myself... (I usually use cron)

---

