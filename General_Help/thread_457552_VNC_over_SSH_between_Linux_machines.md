---
title: "VNC over SSH between Linux machines"
date: 2007-05-28
forum: General Help
---

### Post by FastZ on 2007-05-28
Alright guys, I'm about to pull my hair out over this one.  What I am trying to do is VNC (using vncviewer and tightvncserver) between my desktop computer and my server computer that i have running in another room of the house.  I have Ubuntu-Desktop installed on the server for mere ease of use reasons and I have the Remote Desktop settings found under System>Prefs>Remote Desktop configured to accept remote desktop sharing and secured with a password.  Now, I have been reading every thread here that I can think of about VNC and running it over SSH from computer to computer and every one of them are about VNCing from a Windows client.  That's not what I have here in my setup so I'm needing some help.  

I run the following at the command line:

```
vncviewer -via 192.168.1.149 <servername>:0

```and this is the output that I receive:

```
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
ssh: connect to host 192.168.1.149 port 22: Connection refused
vncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:<servername>:5900 192.168.1.149 sleep 20.
```Now, my problem here is apparently, vncviewer is trying to tunnel over the default SSH port (22) which I do not use.  How do I go about making vncviewer tunnel over the port I have assigned to SSH and not the default port 22?

---

### Post by krismatth3 on 2007-05-28
I don't know about the via switch, but what I do (from the command line, because I rarely do it):

```

# ssh -L 5900 localhost:5900 server

```

Then I run:
```

# vncviewer localhost:0

```

Note that you can't run vncviewer from within the ssh session - run it in a seperate terminal.

---

### Post by FastZ on 2007-05-28
Well, I try that.  I have to use the -p switch in my ssh command since i dont use the default port no more and I believe that there's a : between the first 5900 and localhost.  It wouldn't work for me the way you have it there with the space.  Nowhere I looked that was supposed to explain how to do this did it say that you had to run vncviewer from a completely new terminal window.  I'm glad you told me that or I would have just given up hope.  However, I still cant get this to work.  I finally got a password prompt but when I type in my correct password, it gives me an unauthenticated password error or something.  I guess I will go try to make sure my password is correct on the server and then try it again.  Anymore help from anyone will sure be appreciated.  Thanks.

---

