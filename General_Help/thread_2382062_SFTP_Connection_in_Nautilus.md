---
title: "SFTP Connection in Nautilus"
date: 2018-01-08
forum: General Help
---

### Post by jovaine1 on 2018-01-08
Hi, recently my professor gave me access to a machine he owns for  numerical calculations. I don't fully understand the process but it  worked. His machine is in the university, so I had to "ssh" to the  university server and then I would connect to the computer by using the  commands described below.

In the terminal I use:
```
ssh user@ip.goes.here
```

And in Nautilus with Ctrl+L (or connect to server option):
```
sftp://user@ip.goes.here/
```

Everything was fine until I decided to reinstall ubuntu 16.04. I can  still connect to the machine from the terminal and do everything I used to from there,  however, Nautilus won't connect and will show the following message:

[IMG]https://i.imgur.com/0WqIGjD.png[/IMG] 

Any idea why? I use nautilus (3.14.3). Thank you in advance, and sorry for my newbieness.

---

### Post by TheFu on 2018-01-08
Did you load the sftp / gvfs addons for gnome?  I don't remember the package names, sorry.

---

### Post by jovaine1 on 2018-01-10
I tried "sudo apt-get install gvfs-backends" and got a "gvfs-backends is already the newest version (1.28.2-1ubuntu1~16.04.2)." 
Is that what you were talking about? Anyway, the problem persists. Sorry, I'm new to linux.

---

### Post by TheFu on 2018-01-10
Perhaps: [https://ubuntuforums.org/showthread.php?t=1976517](https://ubuntuforums.org/showthread.php?t=1976517)
Just a shot in the dark.
Take a look at the log files and use **sftp user@server** from the terminal. Does that work?

---

### Post by HermanAB on 2018-01-11
Ayup - to debug connections, you need to use the command line to see the error messages.  Otherwise, you will just go nowhere fast...

---

### Post by jovaine1 on 2018-01-11
So, I typed this into terminal 
```
sftp **user@serverip**
```
And got this as feedback
```
ssh: connect to host **serverip** port 22: Connection timed out
Couldn't read packet: Connection reset by peer
```

Does that help?

Edit: Using 
```
sftp://user@server
```

In Nautilus "connect to server", results in the message "You do not have permission to access the requested location". So it's all about talking to my professor then? Thank you for your replies and help.

---

### Post by TheFu on 2018-01-12
You do realize that 'user' and 'server' need to be filled in with the correct values, right?

Also, ssh/sftp/scp and related programs generally have a way to increase debug output - verbosity.  ssh -vvv user@server is common. I didn't look up what sftp uses, but -vvv is probably it.  Check the manpage.  More 'v's means more output.  -v is 1 level.  -vv is level 2, -vvvv is level 4 output. You get the idea.  This is common across many, many, Unix programs.  Others use -d, as in debug.  The manpage for each program would say.

---

### Post by mamanmen97 on 2018-10-31
i have the same problem
like I have to reinstall my ubuntu

[http://inilagu.wapkup.com](http://inilagu.wapkup.com)

---

