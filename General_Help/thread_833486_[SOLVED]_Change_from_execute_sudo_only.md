---
title: "[SOLVED] Change from execute sudo only"
date: 2008-06-18
forum: General Help
---

### Post by iitywygms on 2008-06-18
I have Javahmo installed.
[http://javahmo.sourceforge.net/](http://javahmo.sourceforge.net/)
Everything works fine.  Only thing is that I have to be sudo to execute it.  I would like to change it so any user can execute it.
How can I do that?

---

### Post by iitywygms on 2008-06-18
Okay, maybe I should try this differently.  I want to add a user to my computer.  I do not want them to have administrative rights, but, I have one program that requires sudo password to run correctly. I want them to be able to run this program without entering a password. How can I set this up?

---

### Post by Happy_Man on 2008-06-18
...I don't think there's a way to do that, as it defeats the entire purpose of sudo. Sorry.

---

### Post by iitywygms on 2008-06-18
> **Happy_Man said:**
> ...I don't think there's a way to do that, as it defeats the entire purpose of sudo. Sorry.

Well then can I change jhmo so it runs without having to use sudo?

If I type jhmo start, it says it starts but does not work properly.  If I type sudo jhmo start, it works fine.

---

### Post by suicidejack on 2008-06-18
I think the way to do that is as follows.  Know the path to the the **upper level directory** of the program, I'll just call that *path* in the following code. Copy this code into your terminal and this should allow you to run the program without being a superuser.

```

sudo chown -R *your_username your_username path*

```

Obviously fill in the two spots with your actual user name and this should work.  I just used this today and it worked for me so hopefully it will work for you also.  Here is a link to see what the above code is doing:
[http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)

---

### Post by ibuclaw on 2008-06-18
Silly Happy_Man... ;)

You can tweak the sudoers file to allow the user to run it, no probs!

But first (since visudo now defaults to vi) you have to set it up so it opens in your preferred editor.
```
sudo gedit /etc/bash.bashrc
```
Add these lines to the bottom:
```

export VISUAL=gedit
export EDITOR=nano

```
Replace "**gedit**" with vim, nano, kate, mousepad, any editor you like. Same is with "**nano**", but only replace it with a terminal specific editor, such as vim, emacs or ee.

Now launch visudo in the terminal (NOTE: you'll need to close and reopen the terminal for the above changes to take effect):
```
sudo -E visudo
```
and put in the command
```
Defaults        env_keep = "EDITOR VISUAL"
```
in the file before the **Defaults  env_reset** line.

So this section of the file should now look like this:
```

Defaults        env_keep = "EDITOR VISUAL"
Defaults        env_reset

```
Now, scroll to the bottom of the file and add this line
```
name  ALL=(%root) /path/to/program
```
So it should look like this
```

%admin ALL=(ALL) ALL
name   ALL=(%root) NOPASSWD: /path/to/program

```
replace **name** with the name of the user. and **/path/to/program** with the FULL PATH to the program that you require the user to run.
Save, and quit, and the user will now be able to run the app without the need for a password.

Also, if you wish to make any further changes to the sudoers file at a later date, just use the command
```
sudo visudo
```

Regards
Iain

---

### Post by Happy_Man on 2008-06-18
> **tinivole said:**
> Silly Happy_Man... ;)

You can tweak the sudoers file to allow the user to run it, no probs!

...[snip]
Regards
Iain
Interesting... I didn't know you could do that. Thanks for educating me (though  it's the last day of school, I shouldn't have to learn anything >.<) :p

---

### Post by ibuclaw on 2008-06-18
Yeah, there is a lot more to sudo than what the ubuntu default gives us.
It is infact a very, VERY powerful tool.

I've just made a few spelling adjustments on my original post though... ><
Your quote contains some errors in it (I was typing too quickly and didn't bother checking before I posted the original) :)
Perhaps you should shrink it down just a little bit, so as ppl don't get confused by it.

Regards
Iain

---

### Post by iitywygms on 2008-06-18
I do as outlined above.

when I get to the part about adding 

{Defaults env_keep "EDITOR VISUAL"

in the file before the Defaults env_reset line.

So the file should now look like this:
Code:

Defaults        env_keep = "EDITOR VISUAL"
Defaults        env_reset}

I do not have the line Defaults env_reset line.

This is what I have


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


, what should I do from here?

---

### Post by ibuclaw on 2008-06-18
Oh, so you didn't install Hardy then? (Defaults env_reset is a new thing in Hardy)

Here is the correction, paste this into your file (replace it with everything you have).
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_keep = "EDITOR VISUAL"
Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults
Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Remove me and adjust the params of the line below
name   ALL=(%root) NOPASSWD: /path/to/file

```
Remove the "**# Remove me**" line and set the "**name**" and "**/path/to/file**" up correctly.

Regards
Iain

---

### Post by iitywygms on 2008-06-18
> **tinivole said:**
> Oh, so you didn't install Hardy then? (Defaults env_reset is a new thing in Hardy)

Here is the correction, paste this into your file
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_keep = "EDITOR VISUAL"
Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL


   I do have Hardy installed????
should I do this anyway?

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults
Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Remove me and adjust the params of the line below
name   ALL=(%root) NOPASSWD: /path/to/file

```
Remove the "**# Remove me**" line and set the "**name**" and "**/path/to/file**" up correctly.

Regards
Iain

I do have hardy installed???? should I do this anyway?

---

### Post by iitywygms on 2008-06-18
oops, dont know how I screwed up your original post. lol

---

### Post by ibuclaw on 2008-06-18
If you haven't already done so, the answer is yes, yes you should.

And remember,
replace **name** with the username of the user you wish to grant permissions.
replace **/path/to/file** with the path of the binary/script.

ie: if the appname is "foo" and it is located in /usr/bin/
put in **/usr/bin/foo**. "foo" on it's own will not work/be rejected.

[QUOTE=iitywygms]I do have hardy installed[/QUOTE]
hmmm... I don't know how or why your file is like it is then.
But maybe that is just one of the great mysteries of Ubuntu...

Also, slow-down!
Take things slowly and steadily. There is no need to rush anything. Else you'll just make mistakes and begin to complain when it all goes horribly wrong :wink:

Regards
Iain

---

### Post by iitywygms on 2008-06-18
This is what I have now.

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_keep = "EDITOR VISUAL"
Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults
Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
kevin   ALL=(%root) NOPASSWD: /usr/bin/jhmo




I tried to run jhmo without sudo, it did not work.

To start jhmo I type "sudo jhmo start" in a terminal, supply password, it works
If I type jhmo start, it reads "starting jhmo" then nothing.  I try to connect with my tivo, it does not connect.

Sorry if I sound impatient, I am just trying to get this set up before I have to leave for a week.
I really appreciate the effort and time.

---

### Post by ibuclaw on 2008-06-18
Firstly, are you kevin?
```
whoami
```

Secondly, is the path right?
Run:
```
sudo /usr/bin/jhmo
```
to check that the destination is correct.

Thirdly, sudo -K && env reset
```
sudo -K
env reset
```
Then close and reopen the terminal.

Sometimes requires that you close all terminals first before it takes effect.

But other than that, it should be just fine.

Iain

---

### Post by iitywygms on 2008-06-18
kevin@ubuntu:~$ whoami
kevin
kevin@ubuntu:~$ 

kevin@ubuntu:~$ sudo /usr/bin/jhmo
[sudo] password for kevin: 
Usage: /usr/bin/jhmo { console | start | stop | restart | dump }
kevin@ubuntu:~$ 

I restart the terminal.
Still the same issue.

here is the terminal output of several different attempts

kevin@ubuntu:~$ jhmo
Usage: /usr/bin/jhmo { console | start | stop | restart | dump }

kevin@ubuntu:~$ sudo jhmo
[sudo] password for kevin: 
Usage: /usr/bin/jhmo { console | start | stop | restart | dump }

kevin@ubuntu:~$ jhmo start
Starting JavaHMO...

kevin@ubuntu:~$ sudo jhmo start
Starting JavaHMO...
JavaHMO is already running.

kevin@ubuntu:~$ but in reality it is not working
bash: but: command not found
kevin@ubuntu:~$ so I do this
bash: so: command not found

kevin@ubuntu:~$ sudo jhmo stop
Stopping JavaHMO...
JavaHMO was not running.
kevin@ubuntu:~$ sudo jhmo start
Starting JavaHMO...
kevin@ubuntu:~$  

now it works

I am so confused. Maybe a bug with jhmo???

its bed time for me so I will try again tomorrow.

---

### Post by iitywygms on 2008-06-19
From another post running a similar type of service.

"when the gui couldn't connect to the server, it was because the server was running as root - which created a log file - and the client was run as a normal user that couldn't write to the log file".

Is that something that could be happening here?

---

### Post by iitywygms on 2008-06-19
Anybody have any other suggestions?

---

### Post by iitywygms on 2008-06-19
Got it to work!

this is my visudo now

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_keep = "EDITOR VISUAL"
Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults
Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
kevin   ALL= NOPASSWD: /usr/bin/jhmo start


And for some strange reason that I DO NOT KNOW, If i try to start the service in a terminal, it will not work, BUT if i create a launcher using gksudo jhmo start it works. I do not have to enter a password. Can someone explain this??????

---

