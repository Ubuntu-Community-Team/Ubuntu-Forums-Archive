---
title: "Trouble using gksu's --print-pass mode"
date: 2007-08-30
forum: General Help
---

### Post by theCSapprentice on 2007-08-30
Alright, here's the situation: I am trying to write a script to launch a ssh tunnel and I wanted to use gksu to ask for the password and then send it to the ssh client over stdin. However, every time I run gksu it gives me a long message along with the password. Ssh, being very helpful, takes this message as the password, giving me an error. So, my question is two-fold. One: Is there anyway to remove this message? And If not, is there a better way to do this password-stdin-thing?

Here are the commands I'm using:

```
nathan@Athena:~/Scripts$ gksudo -p -m "Enter your password for this connection"
sn_launcher_context_complete called for an SnLauncherContext that hasn't been initiated
password
nathan@Athena:~/Scripts$ gksu -p -m "Enter your password for this connection" | ssh -l USERNAME -L19001:REMOTE_SITE_B:21 REMOTE_SITE_A cat -
USERNAME@REMOTE_SITE_A's password: sn_launcher_context_complete called for an SnLauncherContext that hasn't been initiated

Permission denied, please try again.
```

You can see what's happening here. gksu DOES print out the password, but not before printing out that message:
```
sn_launcher_context_complete called for an SnLauncherContext that hasn't been initiated
```. Unfortunately, ssh is getting this message before the real password.

Any help in figuring this out would be welcome.

---

### Post by kidders on 2007-08-31
Hi there,

> **theCSapprentice said:**
> I wanted to use gksu to ask for the password and then send it to the ssh client over stdin.Afaik that won't work. You can't use a pipe to send a password to SSH. (At least I really hope you can't!)

---

### Post by theCSapprentice on 2007-08-31
> Afaik that won't work. You can't use a pipe to send a password to SSH. (At least I really hope you can't!)

I would beg to differ. Looking at the result of the commands I ran ( see my first post ) it seems that ssh is receiving information from gksu when it expects a password. However, it gets gksu's little message before the real password. I think if I could somehow stop that message from happening, ssh could get a password from gksu.

---

### Post by kidders on 2007-09-01
Heh... okay then.

You can easily check with something like **echo <password> | ssh <remotehost>**

---

### Post by theCSapprentice on 2007-09-01
Well, huh, that doesn't work. That's really strange. I could have sworn, based on my previous tests that ssh would take a password from a pipe.

It would be nice if there existed a way to graphically open connections like ssh. Although, now that I think about it, there must be. In Gnome you can do a "Connect to Server..." from the menu and it has a graphical password prompt. So unless the Gnome guys use a custom ssh client, they found a way to pass the password to ssh.

----------------------

Ps. I removed the error message given by gksu by redirecting stderr to /dev/null

---

### Post by kidders on 2007-09-01
SSH refuses to accept piped passwords for a reason ... passing passwords around like that is exceptionally unsafe, so it's explicitly forbidden. If you really want to, I suppose you could use expect, but I would opt for key-based authentication, personally ... and eliminate the interactive element of SSH logins altogether.

---

### Post by cwaldbieser on 2007-09-02
> **theCSapprentice said:**
> Well, huh, that doesn't work. That's really strange. I could have sworn, based on my previous tests that ssh would take a password from a pipe.

It would be nice if there existed a way to graphically open connections like ssh. Although, now that I think about it, there must be. In Gnome you can do a "Connect to Server..." from the menu and it has a graphical password prompt. So unless the Gnome guys use a custom ssh client, they found a way to pass the password to ssh.

----------------------

Ps. I removed the error message given by gksu by redirecting stderr to /dev/null

Without looking at the code, I am guessing they might make use of the SSH_ASKPASS environment variable.

---

### Post by cwaldbieser on 2007-09-02
> **kidders said:**
> SSH refuses to accept piped passwords for a reason ... passing passwords around like that is exceptionally unsafe, so it's explicitly forbidden. If you really want to, I suppose you could use expect, but I would opt for key-based authentication, personally ... and eliminate the interactive element of SSH logins altogether.

Why exactly is this considered unsafe?  If the process at the beginning of the pipe gets the password from a user's input (e.g. some zenity dialog or bash read), then how would an attacker get access to it?  

Doesn't a programs like gksudo must do something along those lines?

---

### Post by altonbr on 2007-12-29
I get the same error:
> $ gksudo --print-pass --message="Please enter your password..."
sn_launcher_context_complete called for an SnLauncherContext that hasn't been initiated
*password*

How can I get rid of that sn_launcher* line?

---

