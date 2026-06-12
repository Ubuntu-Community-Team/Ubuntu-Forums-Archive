---
title: "Confused on how to SSH for use with VNC"
date: 2017-12-28
forum: General Help
---

### Post by freeflyjohn on 2017-12-28
I have got SSH (with keys and on a different port) and VNC working so that I can remote control my Ubuntu desktop using the Share Screen app on my Mac.  I also have my own DNS name which is updated by ddclient.

I temporarily opened port 5900 on my router's firewall and I was able to Share Screen from the internet.

But I realise opening port 5900 on the router's firewall is a security risk and have read that a secure method is to use SSH tunnelling, but I don't understand how exactly.

Using the following assumptions:


[LIST]
[*]SSH port is 12345 (instead of the default 22)
[*]DNS is myserver.dynu.net
[*]Username is bob
[/LIST]

Then to connect to the server I would use:

```
ssh bob@myserver.dynu.net -p 12345
```

I have now closed port 5900 on the router's firewall, so whats the procedure and syntax for SSH tunnelling ?

1. I found the following example of port forwarding/tunnelling:

```
ssh -L 5900:localhost:5900 joe@laptop
```

What would the syntax be in my case, bearing in mind that I have changed the SSH port to 12345 ?

Is the following correct ?

```
ssh -L 12345:localhost:5900  bob@myserver.dynu.net
```

2) And at what point do I do request the port forwarding ?

 Is it a) or b) below:

a) From a fresh terminal on the Mac, do I have to connect to the server first using...

```
ssh bob@myserver.dynu.net -p 12345
```

...and only when connected to the server then do I then request the port forwarding using...

```
ssh -L 12345:localhost:5900  bob@myserver.dynu.net
```

**OR**

b) From a fresh terminal on the Mac do I request port forwarding...

```
ssh -L 12345:localhost:5900  bob@myserver.dynu.net
```

---

### Post by TheFu on 2017-12-28
Setup a ~/.ssh/config file with the different port name.  Then you'll never need to remember if -p or -P is needed for all the different ssh-based tools to connect.  I've never seen **any** ssh-based tool that didn't honor the ~/.ssh/config file - rsync, ssh, sftp, scp, sshfs, vim, rdiff-backup, duplicity, and 20+ more.

Of course, you can have both -p and -L options on the same connection.  Might want to use -N as well.  No need for "bob" if that username is the same on the client/Mac.  Unix systems assume the username with all ssh-based connections.

~/.ssh/config is fully documented in the **ssh_config** manpage. Just to be clear, it isn't required, but makes dealing with different usernames, different ports, and funky remote DNS names/IPs accessible using whatever "alias" you like.  It is a client-side config.  

When you have **ssh myserver.dynu.net** working (it should fill in bob and the port for you behind the scenes), then you can add the -L stuff with 5900 on both sides.

Of course, I wouldn't bother using VNC, since it is slow.  x2go is 2-3x faster and has ssh security built into the protocol.  This assumes you even need a desktop, 99% of the time, I use a plain, ssh connection for everything.  Remote desktops are hogs.

---

### Post by freeflyjohn on 2017-12-28
> **TheFu said:**
> Setup a ~/.ssh/config file with the different port name.

Thanks TheFu, but Im not sure how to setup a ~/.ssh/config file with the different port name ?  Would you be able to provide an example please ?

Would the config file be located at ~/.ssh/ on the Mac or ~/.ssh/ on the server ?

On the server I changed the port number (from the default 22) in /etc/ssh/sshd_config

---

### Post by freeflyjohn on 2017-12-29
No problem I have installed X2go which is now working, thanks for pointing this out :)

I agree most of the time you use shell to connect to the server but its nice to have the option to use remote desktop for things that you can't do in shell

---

### Post by TheFu on 2017-12-29
If this is [solved], please mark it so using the "thread tools" to help others in the community.

---

### Post by HermanAB on 2017-12-29
VNC is basically a Windows thing used mainly by newbies...

On a Mac, you can install Xquartz and then use SSH with X forwarding to launch a remote instance of a file browser.

For example:
$ ssh -Y user@server nautilus

Then you can launch other programs with the click of a mouse.  You don't need to remote the whole GUI catastrophe - you already have a perfectly good one on the Mac.

---

### Post by TheFu on 2017-12-29
Herman, you must have an amazing internet connection, since remote X11 really needs a 100Mbps connection to work nicely.  Anything less and it is painful.  IMHO, even VNC over a full VPN isn't THAT bad.

OTOH, for running a remote GUI tool on another system on the same LAN, *ssh -X* is my default as well.  There were important differences between using ssh -X and -Y previously, so be certain to review those options and pick the one that applies to your requirements.  Just re-re-read the manpage and it seems that on Debian, both -X and -Y have similar behaviors due to lots of apps crashing. Seems they both disable ForwardX11Trusted. Ouch.  Nobody expects X11 to be very secure, but disabling the tiny bit of security it has doesn't seem bright to me.  Regardless, ssh should protect us.

---

### Post by HermanAB on 2017-12-30
"remote X11 really needs a 100Mbps connection to work nicely" Only if you forward the whole remote desktop catastrophe with VNC.

That is why I said, run only the program you want to run *on your local desktop*.
$ ssh -Y user@server nautilus

You don't need VNC.

However, on a Mac, you do need XQuartz, since a Mac doesn't use X.

---

### Post by TheFu on 2017-12-30
My experience with remote X11 is clearly different than yours.  Running a simple xterm over the internet using ssh forwarding is painful here.  I do it about once a month to show people new to Linux how great remote X is on the LAN, but how terrible it is over a WAN connection.  Perhaps your WAN connections are 100Mbps?

The OP is pretty clear that he is going over the WAN. Why else would router ports be forwarded?  BTW, he should only open the ssh port, nothing else. Definitely not the VNC port.

Regardless, we each have different experiences doing things and often come at the same problem from completely different angles.

---

### Post by HermanAB on 2017-12-30
With SSH, you don't run X over the network.  SSH forwards the remote X API over the network to the local X server. For that to work, you need a local X server.  Linux and BSD generally has an X server, but a Macintosh and Windows doesn't.  

Therefore you need to launch a local X server before your start your SSH session.  On Windows, you can use Cygwin.  On a Mac you need Xquartz.  Once that is running, SSH with X forwarding works the same as on Linux or BSD.

The reason VNC is slow, is because it sends a huge amount of useless graphical data over the network.  If you use SSH with X forwarding of a single application, it is not slow and will work much the same as normal.

Something like this is quite usable:
$ ssh -Y -C -c blowfish user@server "gedit filename"

and will pop up the remote gedit with the remote file on the local desktop.

The OP uses a Macintosh.  Therefore, he needs to run Xquartz before he does the above.  If it was a Windows user, then run Cygwin before the above. That's all there is to it and there is no need for VNC.

---

