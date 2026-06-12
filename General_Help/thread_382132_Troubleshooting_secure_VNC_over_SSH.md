---
title: "Troubleshooting secure VNC over SSH"
date: 2007-03-11
forum: General Help
---

### Post by mjskia1 on 2007-03-11
I'm trying to securely tunnel a VNC connection through SSH in order to access my Kubuntu box while I'm out of town for a week.  I've got command-line SSH working and can get onto a shell just fine, but that's as far as it goes.  I've installed vnc4server (and configured ~/.vnc/xtartup to use startkde), but no luck so far.

Here's what I've tried:
On the remote machine (my Kubuntu machine)
```
vnc4server -localhost
```
Unless I'm mistaken, this will start the VNC server and only allow connections from the localhost, right?

Then, on the local machine (a Fedora box)
```
ssh <kubuntu_address> -L  5903:localhost:5903
```
Then, in a separate terminal,
```
vncviewer localhost:3
```

This causes an error message to appear in my SSH session on the Kubuntu computer, telling me
```
channel 3: open failed: connect failed: Connection refused
```

Any idea what I need to do in order to fix this?

---

### Post by cosmolee on 2007-03-15
I set up remote access to my Ubuntu box via VNC in a slightly different way, but this may work for you - it was pretty straightforward.  To set up your Ubuntu VNC server, go to System->Preferences->Remote Desktop (do whatever is equivalent for Kubuntu).  Follow the instructions per: 

[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)


Pay attention to the note that I appended to the article: 

Quote:

Everything went as written except where I enter the IP address of the host I’m trying to access.

In your example you used:

vncviewer -fullscreen xxx.xxx.xxx.xxx:0

But I had to use:

vncviewer -fullscreen xxx.xxx.xxx.xxx:1

instead.

:endquote

As the following referenced article points out, Windows machines generally use :0, Unix machines generally use :1 or :2.

The above is all done on the local network - this confirms that you've got VNC working properly on your server.  Once you get that confirmed, you can then try to access from a remote location.

Follow the instructions from:  [http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html](http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html)

The article is very clear, so I won't repeat what it says, you should be able to follow it easily.

One possible error I noticed in your command line:

```
ssh <kubuntu_address> -L  5903:localhost:5903
```

should be:

```
ssh  -L  5903:localhost:5903 <kubuntu_address>
```

Also, as I indicated in my note to the first article, on my Ubuntu server, the display # was ":1", not ":0" - you MUST get the display # right - you should have figured this # out already when you were doing local-network troubleshooting.   If this is the same for your Kubuntu machine then you would modify the line to:

```
ssh -C  -L  5903:localhost:5901 <kubuntu_address>
```

Notice that I also added the "-C" option to `ssh` to enable compression, this will speed things up on slow lines.  

Also note from the VNC article that they recommend the -encodings "copyrect hextile" option to improve VNCviewer performance.    So, the command line on the remote would be something like:

```
vncviewer -encodings "copyrect hextile" localhost:3
```


Keep in mind that when you are troubleshooting on the local network, the server IP address is going to be different from when you are accessing it from outside the network if the server is behind a router using a local network IP #.  Also, the router must be forwarding SSH traffic to the server you wish to access.  In such a case, the ssh "<kubuntu_address>" you referenced previously is the external IP address of your router.   These are prerequisites to this VNC setup working.


I'm using this VNC setup where my Ubuntu server has only 384kb upload bandwidth, and the remote VNC performance is quite usable.  

The best thing is that I have one persistent GUI desktop.  I'm actually at a local cafe now, VNC-ing into my desktop machine from a laptop, and posting this message.  I could shut down my laptop now and continue the post when I physically get back to my desktop or VNC in from another remote location.  Working this way I never have to lose my place between being remote and at my desktop machine.   Just VNC in, and you're exactly where you left things!

HTH!

---

