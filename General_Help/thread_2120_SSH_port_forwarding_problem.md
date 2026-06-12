---
title: "SSH port forwarding problem"
date: 2004-10-25
forum: General Help
---

### Post by slacker on 2004-10-25
I hope I'm posting this in the right forum.

Switching from Slackware 10 to Unbuntu I've run into a problem with using SSH to forward local ports.  On Slackware the command

ssh -v -g -L 2010:mastercontrol:6010 its -l username

works fine  ( "mastercontrol" and "its" are my hosts file)
I'm using ssh to forward VNC sessions.

SLACKWARE 10

debug1: Connections to local port 2010 forwarded to remote address mastercontrol:6010
debug1: Local forwarding listening on 0.0.0.0 port 2010.
debug1: channel 0: new [port listener]
socket: Address family not supported by protocol
debug1: channel 1: new [client-session]
debug1: Entering interactive session.


But on Ubuntu I get the error:

bind: Address already in use

Looking at the debug out of SSH you'll notice the extra line (in red).

Local forward listening on :: port 2010

This line does not exist on the Slackware SSH output.

UBUNTU

debug1: Connections to local port 2010 forwarded to remote address mastercontrol:6010
[COLOR=Red]debug1: Local forwarding listening on :: port 2010.[/COLOR]
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 0.0.0.0 port 2010.
bind: Address already in use
debug1: channel 1: new [client-session]
debug1: Entering interactive session.

Can any one tell me out to get the SSH client to accept connections back from th e VNC server?  I can' find anything amiss in any config file I'm familiar with.   I'm much more familiar with Slackware than Debian so I'm probably missing something obvious.

Thanks for any help.

---

### Post by jdong on 2004-10-26
Please remove the -g option.

Also, this really isn't a "security" topic.

---

### Post by slacker on 2004-10-26
[QUOTE=jdong]Please remove the -g option.

Also, this really isn't a "security" topic.[/QUOTE]


Sorry, it was late. 

Anyway, if you remove the -g option VNC does not work.

I would really like to know why Unbuntu is binding first to address :: port 2010 and then trying a second time to bind to localhost::2010.

Any help would be greatly appreciated.

---

### Post by slacker on 2004-10-27
This problem turned out to be a good example of why being experienced in a couple of Linux distros (Slackware and Gentoo) doesn't mean you have  a clue when it comes to a third.

The problem had **nothing whatever** to do with port forwarding.  To understand this stupid mistake you only have to remember two things:

1. Slackware sets up non-root accounts so that your current directory is on your path.

2. Just because Slackware doesn't install a VNC viewer doesn't mean Ubuntu doesn't.

I use RealVNC for the remote connections.  In the VNC directory I was used to typing the "vncviewer" command  **without** a leading "./" in front.  You can probably guess what happened.  The Ubuntu VNC viewer started up.  Normally this will not be a problem.  It can talk to the RealVNC server. 

From the SSH command you can see that this connection is forwarded to another computer.  That computer forwards it again to another one down the line.  

After finally using Ethereal I found out what was going wrong.  RealVNC will let you connect to a port other than 5900 by using a double colon in the command string like this:

./vncviewer localhost::6010

Apparently the VNC viewer installed by Ubuntu does not.  Ethereal showed that it was still trying to connect at port 5900, which was rejected by the third computer in the chain.  Which finally clued me in that the wrong VNC viewer was running.   Putting a "./" in front of the command solved the problem.  

Duh.

BTW, if you want to run RealVNC on Ubuntu grab the libstdc++ libraries from a Slackware box and copy them into the /usr/lib directory.  Then it will run fine.

---

