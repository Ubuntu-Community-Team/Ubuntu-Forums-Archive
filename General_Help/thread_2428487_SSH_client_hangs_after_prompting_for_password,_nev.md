---
title: "SSH client hangs after prompting for password, never reads password typed."
date: 2019-10-04
forum: General Help
---

### Post by jwbrase on 2019-10-04
As of today, whenever I try to ssh out from my user account on my main desktop, the ssh client hangs right after prompting for my password. When running with the -v option, nothing is printed after the password prompt, whether or not I enter a password. When the ssh client is killed, my shell attempts to execute the password typed as a command, indicating that the ssh client did not even attempt to read any characters from the terminal after prompting for the password.

This occurs regardless of the host I am trying to ssh to (I've tried both localhost and another machine on the same subnet), and only affects outbound connections using the OpenSSH client. Inbound connections work fine, as do connections with other ssh clients on the same machine (PuTTY). It also only affects ssh processes run by my user account: opening a root shell and ssh-ing to $MY-USERNAME@localhost works fine, running ssh under my own user account and ssh-ing to $ANY-USER@$ANY-HOSTNAME results in a hang. Gksu works fine, as does a text login on /dev/tty1. I haven't yet tried logging out of my X session and logging back in: I'm a bit nervous that if it's something like a PAM issue I could end up locked out entirely (though the fact that gksu and tty1 work argues against this).

While writing this, I've discovered something that makes the issue less severe but more bizarre: The issue *also* affects sudo, but *only* affects either ssh or sudo on the two terminal sessions I first discovered it on (which were actually running on *different* terminal emulators), and does not affect either new sessions or other sessions that were already running when I discovered the issue.

Has anyone ever encountered anything like this before? It seems like just closing the affected terminal sessions is my workaround, but I'm a bit nervous that there may be some deeper issue at play.

---

### Post by Skaperen on 2019-10-05
learn how to run a command through [COLOR=#006400][FONT=courier new]**strace**[/FONT][/COLOR] with the trace going to a file (the -o option).  maybe this can show you or us where [FONT=courier new]**ssh**[/FONT] stops.  it won't work for [COLOR=#006400][FONT=courier new]**sudo**[/FONT][/COLOR] since [COLOR=#006400][FONT=courier new]**strace**[/FONT][/COLOR] denies [COLOR=#800080][FONT=courier new]**suid**[/FONT][/COLOR] privileges.[COLOR=#006400][/COLOR]  i have only encountered this when [COLOR=#006400][FONT=courier new]**ssh**[/FONT][/COLOR] can't complete a connection to the remote host.  but if it prompts for a password then it has connected.

---

### Post by TheFu on 2019-10-05
Both sudo and ssh check the local hostname.  Has that been touched?  It should be both in /etc/hosts and in the /etc/hostname file.
Try
```
$ ssh -vvvv  user@host
```
More 'v's, more output.

Troubleshooting ssh: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

