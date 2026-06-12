---
title: "VNC or FreeNX on Ubuntu 13.04"
date: 2013-08-14
forum: General Help
---

### Post by R0BiN on 2013-08-14
Hi all, I'm sure this is an incredibly stupid question, but I haven't really gotten answers the the world wide web that have made it clear to me (1) whether or not there is and answer and (2) what the fix is.

I have a remote server running Ubuntu 13.04.  I was first using x11vnc and the "vncserver" commmands to create VNC sessions I could then log in to from my Mac using VNC Viewer.  I heard FreeNX was better, more secure, and seemed to have fewer issues with log files essentially filling up all available space (in my case the log files were getting to be hundred of GiBs). I've been using FreeNX server on my Ubuntu 13.04 server, and have been conecting to that from my Mac using OpenNX.

My problem, really, is that when things go wrong and the VNC server either goes rigid (and I have to end it and either try to resume it or terminate it and start a new one) it essentially means I have to start up a large number of programs again.  Whenever I have to resume a session, it seems many of the words and whatnot from the programs and Unity interface don't end up showing up again (further hamstringing me, and meaning I have to just completely start over again).  I also liked that with VNC I could log in as my root user and have all the files/applications being downloaded and installed in the 'correct' (for me) places.  The terminal also seems a bit wonky when I connect through FreeNX; but that isn't something I've explored much of yet.

The log seems to get so huge so quickly because of burte-force attempts.  Is there some way I can get x11vnc (or whatever vnc server you suggest) to either (1) control the size of its log or (2) not log anything?

Is there a program (with a guild on setting it up) that will ban the IPs from the people attempting to brute-force their way in and then will mean I can eventually use my VNC in peace?  (Bonus points if the program can do this without having to deal with HUGE log files even at the beginning.)

Thanks in advance for any help!  If you need more information please let me know and I'll do my utmost to provide it.
x

---

### Post by steeldriver on 2013-08-14
If you want to use x11vnc outside of your own LAN, then you should set it up to only connect via an SSH tunnel (FreeNX does all that for you, under the hood, I think - hence why you don't have the logs full of malicious connection attempts)

Or if you are using the regular ubuntu-desktop (not lubuntu / xubuntu / whatever) then you could use the built-in 'Desktop Sharing' (vino-server) - again you should secure it via SSH if it is exposed to the public net 

You can add something like fail2ban on the SSH service to further secure it against brute forcing

---

