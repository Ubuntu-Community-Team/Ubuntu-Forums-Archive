---
title: "Remote administration behind firewall?"
date: 2006-12-10
forum: General Help
---

### Post by madcow72 on 2006-12-10
I just convinced my brother to delete Windows and install Kubuntu 6.10 on top.  I'm trying to guide him through getting normal functionality to his computer and internet browsing (DVD playback, W32 codecs, Flash, etc.) but he is running into some trouble.

I feel competent enough at Linux by this point to manage my own computer and troubleshoot, but doing it from afar is difficult, so I want to set up a remote desktop connection to take control of his computer.  However, he's behind a router and firewall and has a generic 192.168.... IP address, so invitations using Krfb Desktop Sharing don't actually connect.  Is there some way to get around this?  Is there a better way to connect to his computer to enter commands and administrate?  

Thanks for any help!

---

### Post by Ramses de Norre on 2006-12-10
For just commands: set up ssh, allow port 22 on the firewall and forward port 22 on the router to his local ip.

For the problem you're now trying: search which port it uses and open and forward it.

---

### Post by Azakus on 2006-12-10
I would use PuTTy to administer behind the firewall. I like it better than just a plain terminal and it can forward X.org for any graphical stuff you'd need to do.

---

### Post by madcow72 on 2006-12-10
Ramses de Norre, thanks for your response!  I'm sorry to say I've never done anything like this before and don't know how to port forward.  Neither of us have access to his router because he's on a school campus.  How can I check his port number?  If you don't mind, can you provide me with specific commands?  I'm very much a noob at this sort of thing.  Thanks again!

---

### Post by madcow72 on 2006-12-10
Azakus, 
Thanks for your help too!  I just installed PuTTY, which I've heard of but never used.  Do you know what information I need to have from my brother's end to make a connection?

---

### Post by Ramses de Norre on 2006-12-10
You can't forward a port without access to the router, I'm not sure whether you can connect to him from your side then.... their could be methods to do so though.

---

### Post by technodigifreak on 2006-12-10
Setup reverse VNC, it will allow you to take control of any machine with an active internet connection that is running a GUI (Windows, Linux, and Mac platform independent).

here is a thread in the "How to..." category on this forum.
[http://www.ubuntuforums.org/showthread.php?t=299489](http://www.ubuntuforums.org/showthread.php?t=299489)

This is an excelent solution for any one who has to do remote end-user support.

---

### Post by madcow72 on 2006-12-18
Technodigifreak, thanks for that link!  It took some time to get that working...somehow x11vnc was NOT in the US repositories.  I walked him through enabling everything, but the package could never be found.  Installing it from Sourceforge somehow did not give a command line executable for x11vnc, either!  In the end, I switched him to the Canadian repositories and finally x11vnc was found through aptitude search, then we installed it, and from there on out the tutorial worked like a charm.  This reverse vnc stuff is very very cool.  Thanks again!

(Anyone know why x11vnc can't be found in the US repositories?)

---

### Post by fakie_flip on 2007-05-20
x11vnc can be used for a reverse connection without any ports being forwarded on the computer that is sharing the desktop. How can the same thing be done with ssh? I want a reverse ssh connection. Thanks.

---

### Post by madcow72 on 2007-05-22
I'm not an expert in ssh, but I believe my friend does this with the -R option.  ie.   ```
ssh -R 2222:localhost:22 user@site.com
```   This will open up port 2222 on the remote machine, and forward any connections to your local host on port 22.  You can read more in the man file:

-R [bind_address:]port:host:hostport
             Specifies that the given port on the remote (server) host is to
             be forwarded to the given host and port on the local side.  This
             works by allocating a socket to listen to port on the remote
             side, and whenever a connection is made to this port, the connec&#8208;
             tion is forwarded over the secure channel, and a connection is
             made to host port hostport from the local machine.

That's about all I know, however.  Never actually used it other than connecting to his server so that he could control my box.  (Back when I was really noobie.)

---

