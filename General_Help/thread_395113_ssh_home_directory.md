---
title: "ssh home directory"
date: 2007-03-27
forum: General Help
---

### Post by leptogenesis on 2007-03-27
Hi all,

I was trying to write a script that will open a terminal window, log on to an ssh connection, and then change the working directory in ssh (so a user can start working in that remote directory).  I've gotten this far:

exec gnome-terminal -x ssh my.host.net

and the man pages for ssh mention:

"If _command_ is specified, it is executed on the remote host instead of a login shell."

I'm not sure how to interpret that...it seems like I should be able to execute an arbitrary command (like "cd new/working/directory"), but I can't figure out how to make it work.  Any ideas?

---

### Post by kidders on 2007-03-27
Hi there

> **leptogenesis said:**
> the man pages for ssh mention:

"If _command_ is specified, it is executed on the remote host instead of a login shell."

I'm not sure how to interpret that.Essentially, that means your command would be executed, but not in a shell, which is not quite what you want.

This isn't either, but depending on *why* you want to have certain commands executed on login, it might work for you. I mention it because it's easy and fast...

Imagine one of your users is tired of having to type the same stuff over and over, each time he uses your system. Assuming he's using Bash, you could add some commands to ~/.bashrc. Anything you put in there gets executed when Bash (a shell) starts up. For example...```
if [ -n "$SSH_TTY" ]; then
        cd /var/www
fi
```... would send the user to /var/www, but only if he was logged in over SSH, rather than using a local terminal.

Is that any help?

---

### Post by leptogenesis on 2007-03-27
Not exactly...the idea is that the script will dynamically specify the directory where the shell will end up.  And I should also mention, I can't change the configuration on the server.  It's not mine.

Thanks for the reply, though.

---

### Post by kidders on 2007-03-27
> **leptogenesis said:**
> Not exactly...the idea is that the script will dynamically specify the directory where the shell will end up.Damn. I was afraid of that. :-(

This isn't a very good general solution, but it should probably answer your specific question. For some reason, executing remote commands *and* holding onto a remote shell is trickier than it seems!

**ssh -tt hostname "cd /path/to/wherever && /bin/bash"**

If you wanted to, you could add something like this to /usr/local/bin, and call it something like "start_at"...

```
#!/bin/bash
ssh -tt hostname "cd $1 && /bin/bash"
if [ $? -ne 0 ]; then
     echo "No such directory on remote host: $1"
fi
```

Well... you get the idea.

---

### Post by Mr. C. on 2007-03-27
[ deleted ]

---

### Post by kidders on 2007-03-27
> **Mr. C. said:**
> [ deleted ]

Aw :-( It's a pity you deleted that post. It contained a lot of detail I was too lazy to type in mine! Perhaps you might resurrect it. Hehe.

---

### Post by Mr. C. on 2007-03-27
I'll pass.  It was incorrect advice; I'd forgotten about the -tt option.  Your solution is a good one;  I was going to suggest a function, placed in a global bash profile, but i like your command better.

MrC

---

### Post by leptogenesis on 2007-03-28
> **kidders said:**
> **ssh -tt hostname "cd /path/to/wherever && /bin/bash"**

Hey, it works!  Thanks for the help.  I have no idea what's going on, though...the -tt option isn't in the man pages.  Could you explain what the command's doing?

---

### Post by Mr. C. on 2007-03-28
When you make an SSH connection, either a shell is started, or a command is run.  When the latter, no input terminal is associated with the program, so you wouldn't be able to say:

 ssh remotehost vim somefile

as vim would have no controlling terminal.  This is what I started to say yesterday, but forgot about the -t option (search for -t, you'll see the reference to multiple t's).  The -t option allows a pseudo-terminal to be associated with the command, so you could run the command above as:

 ssh -tt remotehost vim somefile

MrC

---

### Post by kidders on 2007-03-28
**Edit:** Eep... Mr C beat me to it. Hehe.

> **leptogenesis said:**
> I have no idea what's going on, though.
Hehe... that's why I was disappointed to see Mr C's post vanish. :-P The full explanation is quite long-winded.

Essentially, it's important to realise that gaining access to a remote host over SSH does not guarantee you a shell. (A shell is an application that executes commands on a computer based on what you type into its interface.)

To help you understand what's going on, compare the following. I'm SSH-ing into a machine called "frankenstein" from a machine called "stephen-wired"...

```
stephen-wired:~ kidders$ ssh frankenstein ps
  PID TTY          TIME CMD
 8056 ?        00:00:00 sshd
 8057 ?        00:00:00 ps
stephen-wired:~ kidders$
```

```
stephen-wired:~ kidders$ ssh frankenstein
Linux frankenstein 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Mar 28 19:25:35 2007 from stephen-wireless
kidders@frankenstein:~$ ps
  PID TTY          TIME CMD
 8061 pts/0    00:00:00 bash
 8062 pts/0    00:00:00 ps
kidders@frankenstein:~$
```
In the second example, **ps** shows that a "bash" process has started, and is attached to a terminal.

Anyhow, it would normally be inappropriate for the remote host to allocate a pseudo-terminal to you when you're passing a command to SSH, but you can force it to do so anyway, if you want to.

> **-t**
Force pseudo-tty allocation. Multiple **-t** options force tty allocation, even if ssh has no local tty.(From the man page.) Writing "-tt" is the same thing as writing "-t -t".

If you analyse it, the command I posted is actually quite inefficient. You see, **cd** isn't really a command at all ... it's a "shell built-in" (ie it's a facility internal to Bash, that wouldn't necessarily be provided by any other shell. In practice, of course, it is.). So, the sequence of events goes a little like this:

[LIST=1]
[*]Initiate an SSH connection with the remote host.
[*]Force allocation of a pseudo-terminal and start up a shell.
[*]Execute "cd /path/to/wherever".
[*]Only if the "cd" command is successful, execute "/bin/bash" (ie start up another shell, running from within the first one).
[*]Because Bash doesn't change the working directory automatically when it starts (ie the reason you always wind up in "~" isn't because Bash "likes" it that way), you wind up in /path/to/wherever.
[/LIST]

Sorry for rambling... I hope that makes sense!

---

### Post by leptogenesis on 2007-03-28
Hmm...it does seem like that's a bit inefficient, but as long as it works I'm happy.  Thanks guys!

---

### Post by Mr. C. on 2007-03-28
The shell is exec'd no matter what; it has to be so that globbing works correctly:

```
ssh somehost ls '*.c'
```

Effectively, either the shell is run, or the shell with the -c argument is run to run the command.

MrC

---

### Post by kidders on 2007-03-28
> **Mr. C. said:**
> Effectively, either the shell is run, or the shell with the -c argument is run to run the command.Indeed, you're right. Thanks. :-)

---

