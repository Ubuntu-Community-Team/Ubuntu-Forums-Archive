---
title: "vnc server problem"
date: 2007-11-21
forum: General Help
---

### Post by fm1234 on 2007-11-21
Hi,

I tried to configure vnc4server as indicated in [HOWTO: Set up VNC server with resumable sessions]("http://ubuntuforums.org/showthread.php?t=122402") but I get the following error in syslog:

xinetd[6198]: warning: can't get client address: Transport endpoint is not connected
xinetd[4995]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.

I managed to have this configuration working in the two previous versions of Ubuntu, but not with 7.10. I spent already two long evenings searching for clues and trying all kinds of options.

A possible cause for the error is extensively reported in [vnc4server does not start Desktop environment after security update]("https://launchpad.net/ubuntu/+source/vnc4/+bug/78282") and it appears to be solved.

However, in spite of whatever I try, I keep get this error. Any suggestions? 

what about alternatives to connect from Windows to Ubuntu? (I don't want vino). What about Xming?

TIA,
Fernando

---

### Post by blop on 2007-11-21
what about the "allow remote login" thats what i use...

Administration > Login Windown > Remote (tab)

select "same as local"

will work fine on LAN but may need port forwarding on WAN

---

### Post by fm1234 on 2007-11-22
That's what I have. What configuration do you have for vnc server? I'm using xinetd with vnc4server.

Fernando

---

### Post by fragos on 2007-11-22
vncviewer is the default client.  Ubuntu loads a server when you configure for remote desktop.  No configuration should be required other than the remote desktop GUI. I use both NFS and VNC between my laptop and desktop on my LAN.  There is no vncserver running running but vnc with vncviewer works correctly.  Perhaps your problem is with the vncviewer command.  My laptop has the host namr "dell' and the command I use is "vncviewer dell.local.".

---

### Post by jaywatkins on 2007-11-22
Hello - I am having the same problem,  I used the GUI tool to configure vnc to my installation.  I then tried to use 'Chicken of the VNC' from my MacBook Pro to connect to the Ubuntu machine's IP address.  I applied the vnc password, which is different than my user password, over port 1 (5901).  The server kicks back all connection attempts each and every time.  Are there any other settings I could configure?

Thanks

---

### Post by djtm on 2007-11-22
Okay, this does not fix your problem, but *might* help you: Why not try out NXServer, eg the one from [www.nomachine.com](www.nomachine.com) or freenx.berlios.de instead. I believe the first one is easier to install.

---

### Post by daflame on 2007-11-22
I second the motion to use FreeNX.  It still runs fast even under slower connections and the color depth need not be greatly impacted to get performance from it.  I have a forum that has packages of FreeNX for Gutsy.  Just go [here]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx") to download the debs.

---

### Post by fm1234 on 2007-11-23
In nomachines it says freeNX is "A complete solution for remote access to your Unix workstation. It allows 2 concurrent users to connect no matter what their location is, and share the desktop."

I'm not sure this is what I'm looking for, which is to have a user logged in **locally **and a **different** user logged in **remotely **from a Windows (98SE) computer.

And it seems weird to use a virtual machine to do it (is this the case?). Is it faster than VNC?

Care to clarify?

---

### Post by djtm on 2007-11-24
In my experience NX is much faster than VNC.
And the great thing is: You have the choice:
You can:
1. mirror your running display (like VNC)
2. open a new session (as same or different user)
3. open and share a new session (all see the same).

You can also pause and resume your sessions.

And it is very fast and very secure (SSH-encrypted).

Btw. it is _not_ a virtual machine. It acts like a virtual X-server you could say. But that's not much different from VNC. It is very fast and does not slow you down.

---

### Post by djtm on 2007-11-24
And what they mean by "2 concurrent users" is that it has a two-user-limit in the Nomachine free version.
(FreeNX does not have this limit, but is harder to install, maintain and can not share your running desktop easily AFAIK).

NX Server Free Edition -> Nomachine.com
FreeNX -> OpenSource freenx.berlios.de

---

### Post by fm1234 on 2007-11-25
Thanks for the clarifications. I'm still trying it but I get an authentication problem as I reported in the nxserver [thread]("http://ubuntuforums.org/showthread.php?p=3837107#post3837107") above.

```
NX> 148 Server capacity: not reached for user: user123
NX> 105 listsession --user="user123" --status="suspended,running" --geometry="1280x1024x16+render" --type="unix-gnome"
NX> 127 Sessions list of user 'user123' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        DACCC0BFC8331D4A98EBAA0A49A9CA42 --------       1280x1024      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: user123
NX> 105 restoresession  --link="lan" --backingstore="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="X0 (Local)" --type="unix-gnome" --geometry="1024x768" --client="windows" --keyboard="pc102/pt" --id="DACCC0BFC8331D4A98EBAA0A49A9CA42" --resize="1" 

cat: /var/lib/nxserver/db/running/sessionId{DACCC0BFC8331D4A98EBAA0A49A9CA42}: No such file or directory
cat: /var/lib/nxserver/db/running/sessionId{DACCC0BFC8331D4A98EBAA0A49A9CA42}: No such file or directory
NX> 280 Exiting on signal: 15
```

---

