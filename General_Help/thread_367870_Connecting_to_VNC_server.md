---
title: "Connecting to VNC server"
date: 2007-02-22
forum: General Help
---

### Post by al_scott on 2007-02-22
I need to connect to a Windows computer which is running VNC Personal edition on Windows ([www.realvnc.com)](www.realvnc.com)). This version of VNC uses encryption, so I can't connect to it using standard VNC.

I downloaded the VNC Enterprise viewer gz file from the realVNC site, but I can't work out how to install it.

Is there something that I can install from a repository instead?
If not, can anyone help me install the application from the file I've downloaded.

By the way, I have Ubuntu Edgy.

Thanks

Al

---

### Post by ndube on 2007-02-23
You could try running xvncviewer from the terminal, although I do not know if it supports encryption.

If it does not, post the error messages you receive when you try to install VNC Enterprise viewer and tomorrow I will see if I can help.

---

### Post by al_scott on 2007-02-23
Hi ndube

When I try to connect from the terminal, I get this error...
> dad@blacky:~$ xvncviewer xxx.xxx.xxx.176:5900
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 4.0 (viewer 3.3)
VNC connection failed: No configured security type is supported by 3.3 viewer

The file I downloaded from RealVNC.com is called 'vnc-E4_2_9-x86_linux_viewer'. It was originally in a gz file.

I'm new to Linux and can't work out how I'm supposed to install it!!

Any suggestions??

Al

---

### Post by supirman on 2007-02-23
There are directions in the README file in the tar.gz.


Edit:  sorry, I see you said you're new to linux, so save the file to your home directory, then do this in a terminal:
```

cd
tar xzf vnc-E4_2_9-x86_linux.tar.gz
cd vnc-E4_2_9-x86_linux

```

This puts you in the directory where you unzipped the contents of the tar.gz file.

To just run that viewer, you can now:
```
./vncviewer yourhost
```

To install it to somewhere in your $PATH, so you can just run it from any location (/usr/local/bin is a good spot) you would (from inside the vnc-E4_2_9-x86 directory):
```

./vncinstall /usr/local/bin

```

Again, the README has the necessary info.

---

### Post by al_scott on 2007-03-14
I sorted this. It was simple in the end
All I had to do was change the permissions on the file so that it could be run as an executable.

Now, I can just double click on the file and VNC appears!

---

