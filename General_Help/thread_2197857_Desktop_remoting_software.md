---
title: "Desktop remoting software?"
date: 2014-01-05
forum: General Help
---

### Post by junk.here on 2014-01-05
I'd like to know what my options are for connecting to a Ubuntu desktop remotely. As a stretch goal, it'd be great if there's something that can support full motion video with audio at full speed...

---

### Post by jamesisin on 2014-01-05
Sending that kind of data over your network connection requires a lot of bandwidth.  I trust your home network is wired with gigabit ports all around.

Remina is the new client for connecting and I think it's the best so far.  As for serving, you'll look at Desktop Sharing (installed by default).

---

### Post by pqwoerituytrueiwoq on 2014-01-05
if you need something cross platform there is a addon for chromium
[https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=en](https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=en)
there is also teamviewer but it requires 32bt libraries and runs using a custom wine setup

---

### Post by nerdtron on 2014-01-05
Install x11vnc from the software center to your Ubuntu computer. The use any VNC viewer to connect to it via the network. This is what I use to connect to my xubuntu desktop.
Do you use Unity desktop? I remember reading somewhere that there are problems with unity on VNC software.

---

### Post by deadflowr on 2014-01-05
> **nerdtron said:**
> Install x11vnc from the software center to your Ubuntu computer. The use any VNC viewer to connect to it via the network. This is what I use to connect to my xubuntu desktop.
Do you use Unity desktop? I remember reading somewhere that there are problems with unity on VNC software.

If you go this method, which I too have had to do recently, tunnel x11vnc through ssh.
I've found x11vnc a tad bit better than the default vino-server.

---

### Post by zemega on 2014-01-06
TeamViewer, you can connect from Windows, Mac, Linux, Windows Phone 8, iOS, and Android.

---

### Post by QIII on 2014-01-06
I have found the best solution, by far, to be NX and I currently use NoMachine NX 4.0 for remoting.  They even have a Windows NX server version, so you can NX into Windows machines rather than using RDP now.

Windows does not allow SSH, but NoMachine NX uses SSH by default and seamlessly from Linux to Linux.  Do not, do not, do not -- use passwords with SSH.  Use strong keys instead.

No solution is going to give you very good video, despite their claims.  NoMachine 4.0 is the best I have found so far, but it is far from smooth.  But they have solved their problems with audio.

Setup is much easier now, but you still have to attend to making sure you have SSH set up.  NoMachine puts keys in a different set of directories than more familiar SSH solutions in Linux.  Since I did that all under NX 3.5 and didn't have to worry about it for NX 4.0, I'm not sure how difficult it is with the new version.  If you've never set up SSH before, I imagine it might be a bit frustrating.

NoMachine NX is not FLOSS.  NoMachine is a commercial company.  But they make their money on their corporate accounts and they let you download and use the personal bits for free.  NoMachine owns the technology, so even FreeNX and the like are dependent on something that is not really FLOSS.  So consider if that is an issue for you.

---

### Post by nerdtron on 2014-01-06
^^ This one is very good especially if you have many machines to connect to.

---

### Post by junk.here on 2014-01-08
Thanks for the suggestions, everyone. I'll try them out :)

I really don't get why this is so hard on the desktop though - this has already been done in both the consumer electronics space (e.g. Nvidia Shield and Apple AirPlay) and in enterprise VDI (VMware Horizon View and Microsoft RemoteFX), so it's certainly technologically feasible. You'd think that the desktop, which has far fewer restrictions than a smart device and far fewer complexities than a datacenter full of VMs would be a lot further ahead...

---

### Post by jamesisin on 2014-01-09
Of course that View data center full of VM's was built specifically to transmit that data across a network... not so much a desktop.

---

