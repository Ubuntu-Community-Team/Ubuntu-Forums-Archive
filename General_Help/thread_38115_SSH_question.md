---
title: "SSH question"
date: 2005-05-30
forum: General Help
---

### Post by patrik1982 on 2005-05-30
I have a question regarding ssh on ubuntu.

I want to start a torrent-downloading from a remote host using ssh.
By typing

> btdownloadcurses blablabla.torrent

I can start a download.

But if I close the ssh terminal (putty, win xp), then the download will stop?

Is there any way to start a download from a remote host, close the terminal window and still keep the download running?

---

### Post by tonym on 2005-05-30
Try

nohup command  &

The command will then continue to run when you close the session.

Regards

Tony

---

### Post by dare2dreamer on 2005-06-23
you might also have a look at a program called screen.

---

### Post by uglysmurf on 2005-09-14
I'd like to do the something simliar and am also having a tough time...

I'd like to ssh -X to a headless server, and run firestarter, so its GUI is displayed on the desktop I'm ssh'ing from.  However, like the OP, when I close the terminal window I launched from it kills both the GUI and the app.

nohup did not work for me:

> user@desktop:~$ ssh -X h_server
Password:
user@h_server:~$ nohup xeyes&
[1] 26064
nohup: appending output to `nohup.out'
user@h_server:~$ exit
logout 

after this the terminal window remains open, hanging, until I either close xeyes (which closes the terminal window) or close the terminal window (which closes xeyes).

As for screen, I began to read the man page but did not immediately understand how this might help, care to explain further?  

Anyone have any other ideas please?

---

### Post by dare2dreamer on 2005-12-13
In the case of an Xforwarded graphical application, I don't know that there is a way to have the program continue to run once the ssh session is closed out. The ssh session is acting as a tunnel, and without it the application shuts down.

You might look at NX, they recently added support for "rootless windows", meaning forwarding a single application, rather than a whole desktop. It works well enough, though frankly I'm pretty sure that forwarding the entire desktop via NX was faster than running a single application that way.

Screen is an incredibly handy tool that allows you to handle multiple terminal sessions in a single window, remotely disconnect and reconnect from running sessions and all sorts of other cool tricks.

A quick google for screen howto turned up this beginner's tutorial:
[http://nerdierthanthou.nfshost.com/2004/12/screen-howto.html](http://nerdierthanthou.nfshost.com/2004/12/screen-howto.html)

It should give you all the basics.

---

### Post by uglysmurf on 2005-12-17
I know it's a silly workaround, but I now use the GNOME applet "Command Line" to launch apps on other machines where I want the display forwarded to me, but don't want to leave a terminal window open.  So, from the Command Line applet:

```
ssh -X h_server xeyes
```

Also, a useful tip I've since picked up:  If you've SSHed into a machine, and want to kick off a process that will continue to run after you've closed your SSH session, you need to redirect stdin, stdout, and stderr to somewhere (/dev/null works).  For example: 

```
someapp < /dev/null >& /dev/null &
```

NOTE this will not work with apps that use the display, like we were discussing before.

---

### Post by Spyderizer on 2006-01-06
```
mark@argos:~$ nohup btdownloadcurses "blah.torrent" &
nohup: appending output to `nohup.out'
[1] 10421
```

...so what exactly just happened here?

---

