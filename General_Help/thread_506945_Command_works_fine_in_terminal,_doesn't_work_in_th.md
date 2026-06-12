---
title: "Command works fine in terminal, doesn't work in the run command application...!?"
date: 2007-07-22
forum: General Help
---

### Post by sammydee on 2007-07-22
Hi all.

This stupid little problem is driving me mad.

I want to set up a tiny little script that will allow remote connection to a file system on my home server over the network. If I execute:

sshfs [email]user@xxx.xxx.xxx.xxx[/email] ~/remotedrive

on the gnome terminal then it works just fine. I want to make this an application in the applications/internet menu so I can just click it and it will work. I added the command using alacarte, then set it to run in terminal. When I click it, the terminal window comes up fine and it asks for my certificate key. I enter it then the window just exits, and the remote file system is not mounted.

The command fails if I run it from the "run command" dialogue as well. Why is it working in the terminal and not in the run command dialogue!?

sam

---

### Post by happy-and-lost on 2007-07-22
Set it up as an executable script like...

```
 #!/bin/bash
sshfs user@xxx.xxx.xxx.xxx ~/remotedrive &&
exit
```

Don't forget to *chmod +x* the script

---

### Post by Nythain on 2007-07-22
gnome-terminal  sshfs [EMAIL="user@xxx.xxx.xxx.xxx"]user@xxx.xxx.xxx.xxx[/EMAIL] ~/remotedrive
might work... not sure if you will need any quotes in there anywhere... basicall when you open it with the run command dialog box it just runs the command the quits... you need to tell the dialog box to run a terminal session, then tell the terminal session to run the command

edit: or that bash script will work nicely

---

### Post by sammydee on 2007-07-22
Thanks for the replies

Shell script won't work because I need a command line so that I can enter the password.

I tried

gnome-terminal  -x sshfs sam@192.168.0.3 ~/sam-server/

But it opens a window then immediately exits without doing anything useful

any other ideas?

sam

---

### Post by strabes on 2007-07-22
```
sshfs user@xxx.xxx.xxx.xxx ~/remotedrive &
```

I THINK this will work. The difference is the ampersand which tells the process to run in the background. You're running in gnome-terminal, and therefore when it exits, the process is terminated.

---

### Post by eentonig on 2007-07-22
If you control the ssh server, you could set it up that it doesn't require a password, but that it uses the certificate as authentication.

If you can't, you will need to parse your password via the scripts as well. Either hardcoded in the script, or as a parameter you pass with your command.

---

### Post by sammydee on 2007-07-22
The ampersand command didn't work.

I HAVE got the ssh server set up so it uses certificates, I still have to enter the password for my certificate key. I don't like using a blank password because it is insecure.

Sam

---

