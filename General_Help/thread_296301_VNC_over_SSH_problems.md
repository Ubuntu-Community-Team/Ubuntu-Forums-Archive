---
title: "VNC over SSH problems"
date: 2006-11-09
forum: General Help
---

### Post by tonyr1988 on 2006-11-09
I'm trying to do a remote desktop to another computer (right now, it's in my living room - later it'll be in someone's house). I've got SSH and VNC set up (I hope correctly - I followed the guide in the wiki). Here's what I do:

> ssh -X user@address

(I used dyndns.org - is the X-forwarding necessary?)

I can SSH in just fine - it asks my password, and I get the prompt.

On the remote desktop, I opened up "Remote Desktop Preferences" and it looks like this:

> Allow other users to view your desktop (check)
Allow other users to control your desktop (check)
Users can view your desktop using this command:
vncviewer eric-desktop:0

Ask you for confirmation (check)
Require the user to enter this password (unchecked)

So, once I'm SSh'ed in, I do:

> vncviewer eric-desktop:0

And it says:

> VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)
No authentication needed
Desktop name "LibVNCServer"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap and visual, TrueColor, depth 24.

What's weird is that it goes right back to the prompt. Is that normal? On the remote desktop, a box pops up asking for authorization. I click "Allow", wait a little bit, and nothing happens. What do I need to do?

I've never done VNC before, so I'm lost from here.

Thanks!

---

### Post by tonyr1988 on 2006-11-09
Scratch that - after *several* minutes of waiting, the VNC window finally popped up on my computer.

But how long is this supposed to take? I know it's gonna be slow, but it literally takes another minute or more to load what the screen looks like (it goes square-by-square). I clicked something and nothing happened (even after a while). Both computers are good and on high speed connections (in this case, they're even right next to each other :)).

On Windows, they have "Remote Assistance". When I used to be on dial-up, I used my super-old computer to connect to this desktop, and it went faster than this, so I'm assuming I'm doing something wrong.

Any ideas?

---

### Post by arley on 2006-11-09
first off in order to use SSH with VNC, what u actually need to do is port foward your VNC port via SSH. The thing is here SSH uses port 22, while VNC uses port 590x where 'x' is your VNC session. First off you should test if your VNC is working without SSH first. then only do the SSH port forwarding to enable VNC via SSH

---

### Post by jeffathehutt on 2006-11-09
I think the slowness is caused by using vnc **over** ssh.  I haven't heard of anyone else doing this.

Usually, you run either vnc or ssh, not both at the same time.  ssh is used mainly for connecting to the terminal at a remote computer.  While it is possible to do X forwarding over ssh, it is painfully slow.

vnc on the other hand is used mostly to get a GUI on the remote computer.  It operates over unsecure connections, with all the data traveling plain-text over the network.  vnc is not ideal if you are going over the internet, because it is very easy for someone to steal your password.

Your best option may be to use NX.  NX or freeNX operates much like vnc, but it is over a secure line with ssh.  By using ssh, you still get the graphics over the network, but it is much more secure than vnc.  Also, many find NX to be faster than vnc.  Check [http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Access_via_NX]("http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Access_via_NX") for more information about nx.  That guide is for dapper but it works fine under edgy as well.

---

### Post by arley on 2006-11-09
umm most pple that run vnc over ssh is cause the machine is behind a firewall or something like that, it gives you a secured connection thus u dont have to open too many ports on your firewall only the usual port 22, i have been running in this fashion for quite a while now, there is no lagg or anything like that from my experience :)

---

### Post by krismatth3 on 2006-11-09
Actually this is rather common place. Many people do it because a. vnc is not a secure protocol and b. who wants to poke an extra hole in the firewall?

---

### Post by tonyr1988 on 2006-11-09
Well, I figured I'd try NX, since VNC obviously wasn't working. I followed the Ubuntu Guide to the tee, and I didn't get any errors. However, when I run the NX client (in fullscreen mode), the NX logo comes up, the screen goes black, and that's it. Did I miss anything?

---

### Post by krismatth3 on 2006-11-09
The X forwarding is not neccessary. Try something like:

ssh -L 5900:localhost:5900 eric-desktop

Then

vncviewer localhost:0

Edit: whoops, that URL was more windows specific; try [http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html](http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html)

---

### Post by tonyr1988 on 2006-11-09
When I try that, I get an "Error: Can't Open Display"

I've kind of given up on VNC - the few times it works, I can't really do anything when it takes 5-10 minutes to load the screen (and still doesn't register mouse clicks or anything).

---

### Post by krismatth3 on 2006-11-09
Wow, maybe google for "ssh vnc" and peruse some howtos. I've never heard of this kind of problem before.

---

### Post by tonyr1988 on 2006-11-09
I don't completely understand the ssh command using the 5900s. I'm assuming they are ports? If so, do I need to do anything to open them? I forgot to mention I'm going through a router - I'll probably have to forward something, huh? I've got SSH1 for my ssh to work, but what do I need for VNC?

---

### Post by krismatth3 on 2006-11-09
The L switch for ssh forwards a port from the local computer to the remote host, e.g. essentially poking a hole in any firewall. You do not need to modify your firewall if you can get an ssh connection.

-L means "make this port on this computer forward to that port on the specified computer"

man ssh says about -L: "Specifies that the given port on the local (client) host is to be forwarded to the given host and port on the remote side.  This works by allocating a socket to listen to port on the local side, optionally bound to the specified address.  Whenever a connection is made to this port, the connection is forwarded over the secure channel, and a connection is made to host port hostport from the remote machine."

Which leads me to say my original instructions may have been a bit incorrect, try this:

ssh -L 5900:eric-desktop:5900 
..

then, in another terminal (not in the ssh connection!) do this:

vncviewer localhost

I suspect what happened for you before is that since you were using "ssh -X" to connect and then running vncviewer on the remote computer. (It was so slow because it was running on the remote computer with X forwarding, rather than running vncviewer on the local computer.)

---

### Post by tonyr1988 on 2006-11-09
YAY YAY YAY YAY

I feel so retarded. I was doing vncviewer within my SSH session. I opened a new terminal tab, and it works great. Still somewhat slow, but it works - so it's all good. :)

Thanks a ton - sorry for taking that for granted.

PS If I run it in fullscreen, what's the easy way to close it?

---

