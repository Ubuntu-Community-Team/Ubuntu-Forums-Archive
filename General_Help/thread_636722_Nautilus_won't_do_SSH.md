---
title: "Nautilus won't do SSH"
date: 2007-12-10
forum: General Help
---

### Post by tengil on 2007-12-10
Hi. I'm having problems connecting to solaris server with SSH in Nautilus. After entering username and password I get a popup saying "Nautilus cannot display ssh://..." and "Please select another viewer". Runnign Nautilus from the command line I get this:

```

kurt@tavla:~$ nautilus --browser ssh://server_address
Initializing nautilus-open-terminal extension
Initializing gnome-mount extension

(nautilus:7610): gnome-vfs-modules-CRITICAL **: Message length too long: 707406378

```

What could this be?

Gutsy client:
- Linux tavla 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

Server:
- SunOS alf 5.9 Generic_122300-13 sun4u sparc

Nautilus ssh to other ubuntu computers works fine.

---

### Post by tengil on 2007-12-10
Same problem with sftp:
```

kurt@tavla:~$ sftp user@server
Connecting to server...
Authorized uses only. All activity may be monitored and reported.
Password: 
Received message too long 707406378
kurt@tavla:~$ 

```

Putty's psftp just hangs:
```

kurt@tavla:~$ psftp user@server
Using username "user".
Authorized uses only. All activity may be monitored and reported.
Using keyboard-interactive authentication.
Password: 


```

Same thing happens with psftp on windows so it must be a server issue.

---

### Post by Elenion on 2007-12-18
I've a similar problem with sftp.

What I'm trying to do is to SFTP from Ubuntu Gutsy to a Window server. It works fine from console but as I try in Nautilus it just hangs...

What I do in Nautilus is to insert in the taskbar the address:

sftp://user@server.domain

it asks for the password, but after that nothing. The Nautilus window is just stucked and I need to Force the Quit to close it.

Anybody experienced the same problems?

---

### Post by fjgaude on 2007-12-18
I vaguely remember I was having these issues until I realized that both openssh-client and openssh-server was no initially installed in Ubuntu Feisty... I checked in Gutsy and it seems to be.

So make sure you have server installed, and the client. I also have ssh-askpass-gnome installed.

All seem to work well now.

---

### Post by tengil on 2007-12-18
My error was wrong shell at the solaris server for my user. I was setup with tcsh. Switching to bash fixed it. So the problem was on the server and not with ubuntu.

Maybe you could try starting nautilus from a terminal window. It might give you an error message.

```

  $ nautilus --browser smb://user@server

```

You might have to kill off the global nautilus process first though.

---

