---
title: "terminal server client or gnome rdp"
date: 2007-12-08
forum: General Help
---

### Post by gorlando on 2007-12-08
I cannot find documentation on how to use either of the above programs.

all i want is a simple example of what to what to put in the fields on the screen form
for either of the above programs.

I want to connect and control over the internet to a computer that i know the ip address of.
it's another ubuntu linux pc that i have set up through remote desktop preferences to accept remote desktop viewing.

---

### Post by rmemm on 2007-12-08
As far as I know, type in the IP address in the computer field, select the VNC type of connection, then select connect.  I think you'll be prompted for a password if one is needed.

Rob

---

### Post by gorlando on 2007-12-08
using terminal server client, nothing happens on my end.

using gnome rdp i get

TightVNC viewer version 1.2.9

Usage: /usr/bin/xtightvncviewer [<OPTIONS>] [<HOST>][:<DISPLAY#>]
       /usr/bin/xtightvncviewer [<OPTIONS>] [<HOST>][::<PORT#>]
       /usr/bin/xtightvncviewer [<OPTIONS>] -listen [<DISPLAY#>]
       /usr/bin/xtightvncviewer -help

<OPTIONS> are standard Xt options, or:
        -via <GATEWAY>
        -shared (set by default)
        -noshared
        -viewonly
        -fullscreen
        -noraiseonbeep
        -passwd <PASSWD-FILENAME>
        -encodings <ENCODING-LIST> (e.g. "tight copyrect")
        -bgr233
        -owncmap
        -truecolour
        -depth <DEPTH>
        -compresslevel <COMPRESS-VALUE> (0..9: 0-fast, 9-best)
        -quality <JPEG-QUALITY-VALUE> (0..9: 0-low, 9-high)
        -nojpeg
        -nocursorshape
        -x11cursor

Option names may be abbreviated, e.g. -bgr instead of -bgr233.
See the manual page for more information.

---

### Post by gorlando on 2007-12-08
i got a "unable to connect to host" error

i used the ip address with no colon or anything after it.

---

### Post by rmemm on 2007-12-08
One checking question -- you do have to setup the remote desktop on the remote machine by using System>Preferences>Remote Desktop, and then allow connections, and allow control, and choose require user to enter password, and set the password.

Then on the remote system, you must be logged in already.

There are other ways to set this up -- but this is how Ubuntu is configured by default. 

If the remote system is like this -- you should be able to then connect.

Otherthing -- try to "ping" the remote system to make certain you actually have a network link to start with.  You can do this with the "ping" command line command or from the System>Administration>Network Tools dialog.

Rob

---

### Post by gorlando on 2007-12-08
ping was successful.

yes the computer i am trying to connect to was already set up as you stated.

i'm not sure exactly what you mean by "logged in" at the remote computer,
but it was on and the username  and password was entered.

---

### Post by rmemm on 2007-12-08
Strange that should work.

You could try a few different display numbers.  Like I use 192.168.2.41:0, but a :1, :2, etc. version might be worth trying just in case for some reason your system is not using Display 0.  Also -- make sure your using VNC protocol.

Other thing to try -- if you have ssh installed and configured on both sides, try opening an ssh connection.  If your not familiar with ssh -- it allows you to open a remote command line shell from the command line of your local system.  

I don't know what Ubuntu does -- but VNC in general often uses ssh to create the encrypted transport tunnel for VNC.

Other thing you can try -- is to bypass all of the gui stuff and try a direct command line invocation of the vncviewer.  The viewer is called either vncviewer, xvnc4viewer, or xtightvncviewer depending on which VNC package you have installed.

For tight vnc, you could try the command:

xtightvncviewer 192.168.2.41:0

(if you host is 192.168.2.41).  Please note, above is not encyrpted meaning not secure for the internet.  Meaning the session and password keys won't be secure.

If you want more security -- run vnc over ssh with something like:

xtightvncviewer -via 192.168.2.41 localhost:0

I just mentioned the command line stuff as it might help you figure out why you can't connect.

Rob

---

### Post by gorlando on 2007-12-08
thanks Rob.

i ran the xtightvncviewer command
but the screen just sits there.

i'll need to verify that the remote computer is on and logged in but i'm 
fairly certain it is.

---

### Post by rmemm on 2007-12-09
Regarding black screen.  It's possible that that is a good sign.  If you have a screen saver on the remote system, VNC will show that screen saver I think.  You should be able to then unlock your account like you normally do.

Other thing with VNC -- I may be best to set your screen saver to a simple dimming/black rather than some complicated OpenGL graphic -- expecially if your on a slow link.  Other thing -- black screen savers are significanly more energy efficient both in CPU power, and on CRTs because of less beam current and and maybe even on LCDs if it really turns them off.  So black is good for a screen saver in oh so many ways.

Rob

---

### Post by rmemm on 2007-12-09
Other thing I forgot to say -- I have in the past had at least one case where two different versions of VNC were not compatible.  If after you try everything they still don't work, might be worth trying either vnc or vnc4 versions to see if they work better for you (as compared with tightvnc).

Are you using the same version of Ubuntu on both machines?  I ask because several years ago I had difficulty getting something like Redhat 9 and Linspire 4 I think it was to handle a mutual VNC connection.  I can't remember the details at the moment -- it was so long ago.

Rob

---

### Post by rmemm on 2007-12-09
Other thing -- perhaps VNC is set to view only on the remote side -- for example if your screen saver is black and you have vnc to view only -- then black is what you'd see.

Rob

---

### Post by gorlando on 2007-12-09
thanks rob 
but i didn't mean black screen.

i meant that it does nothing.
from terminal server client, i enter computer (ip address)
and protocol (vnc) and click on connect and absolutely nothing happens.

then i get "unable to connect to host" connect timed out (110)


if i use xtightvncviewer no response from a terminal session.

---

