---
title: "xtightvncviewer error connecting when logged in as a different user"
date: 2014-01-05
forum: General Help
---

### Post by goemonburo on 2014-01-05
I have a VNC server running that works fine if I:  1) log in as myself and connect via the commandline "xtightvncviewer" (it prompts me for a server and password, and I'm in).  2) It works fine if I access via a ssh tunnel from somewhere out there on the internet.  3) It works fine from a different machine on my LAN.

However I get an error when I log in as a different user and then try to access it.  It says "server not configured properly" and exits.  Every time.

Anyone out there have any idea what's going on?

Thank you!

---

### Post by steeldriver on 2014-01-05
what user are you running the vncserver as?

---

### Post by goemonburo on 2014-01-06
The same user.  Let's call it User1.  Not root.

---

### Post by steeldriver on 2014-01-06
Maybe I'm misunderstanding what you're trying to do, but the usual way to run remote vnc sessions is 1 vncserver per user, each on a different display # / port # - trying to access a different user's display would normally not be allowed (same as accessing a different user's physical X session)

---

### Post by goemonburo on 2014-01-06
Well this hasn't been what's happened in the past.  And what I have is a family computer on the lan running the User1 server.  But it could be anyone in the family logged in and I want to quickly (without interrupting their session) check my email or whatnot via VNC.  I was able to do this just fine any time I've been using VNC in the past (something like 6 or 7 years).  But somehow this time, it's not allowing it.  I'm not trying to access another user's vncserver, either.  There's only one.  It's just that I'm not logged in as User1 anymore.  It doesn't work if I'm logged in as User2 and try to connect.

---

### Post by goemonburo on 2014-01-06
It seems to totally defeat the purpose of VNC if the only way to access it is by logging out, logging in as User1...then I'm AT my regular desktop and might as well just pull up the normal applications.  I don't think I'm trying to do anything particularly weird here.  Just be logged in as a different user (User2) and connect to the VNCserver on 5900.  If I enter the right port and the right password, it should (as in ought to!) connect and show the VNC session.  I don't know why it wouldn't...

---

### Post by Toz on 2014-01-06
*Moving to **General Help** (not really a virtualization issue).*

---

### Post by steeldriver on 2014-01-06
OK I think I understand what you want to do, and yes that should be possible (I was confused by your terminology "logging on" rather then "connecting")

It may just be a matter of getting the sharing options sorted out i.e.

```

       -nevershared
              Never allow shared desktops.

       -alwaysshared
              Always allow shared desktops.

```

---

### Post by goemonburo on 2014-01-06
Interesting...thank you Steeldriver for the tip.  My understanding of the -nevershared/-alwaysshared option (neither of which I used) was that it allowed multiple connections to stay open.  For example, if I wanted to have several people in different places all looking at the same screen, I could set up a VNC session and give out the password and 3 or 10 or 50 people could all watch at the same time.  In a -nevershared world, the instant that a new connection is made from a different client somewhere, the existing one is terminated.  Thus it protects against someone forgetting that a session got left open and some random person sitting down to an open VNC session as someone unwittingly uses it in a different place.

If I'm wrong then my issue is a different one since I'm easily able to connect from other places, whether or not I've closed the previous client session.  I'd actually LIKE to have the session close automatically if I connect from somewhere else.  But right now, the issue is why can't I connect when a different person is logged in.

Still scratching my head, but I appreciate your help!  If anything else comes to mind, please let me know!

---

### Post by steeldriver on 2014-01-06
Can you describe a bit more the exact setup and who's logged in to what?

For example, here is my current setup:

[LIST]
[*]I'm sitting at a Windows destktop running a PuTTY session to ubuntu-server 
[*]via PuTTY I started my own vncserver on display :5 (port 5905) and user2 (co-worker) starts vncserver on :9 as a shared session 
[*]I have 2 tunnels set up in PuTTY, one tunneling L5905 to localhost:5905 and one L5909:localhost:5909 
[*]I then have 2 tightvnc client connections, one connected to each server (co-worker gives me the VNC password for the shared session) via localhost:5905 and localhost:5909 respectively 
[/LIST]

---

### Post by goemonburo on 2014-01-06
Sure, here's my setup:

1 VNCserver that's on a Lubuntu 13.10 desktop started under xterm via the command "vncserver --geometry 1158x867"  (port 5900).  It was set up by User1 while being logged in as User1.  It's in the family room.  Let's call it "Family Machine."

2.  Still logged in as User1 on "Family Machine," I can connect by typing "xtightvncviewer" from xterm, and I'm prompted for a server and password and it's fine.  

3.  Logged into my "Work Notebook" 20 miles away, a Win7 machine, I can connect just fine by using Putty as an ssh tunnel and typing "localhost:8888" and the password, using REALVnc.

4.  Back home again, logged into my "Home Office" computer (Fedora) downstairs I can access it just fine by the Remote Desktop Viewer application, prompted first for the server, then the password, and it opens fine.

5.  However, if I go to "Family Machine" and User2 or User3 is logged in, I pull up xterm, type "xtightvncviewer" and am promted for the VNC server, which I enter, then the password, which I enter.  But it spits it out saying the server isn't configured properly.

6.  If I then ask User2 or User3 to kindly close all their open applications and log entirely out and log back in as User1, I pull up xterm, type "xtightvncviewer" and am prompted for the VNC server, which I enter, then the password, which I enter, and the session opens up just fine.

What used to happen is that I could do option 5 just fine without problems.  I could be logged in as any user, type "xtightvncviewer" and enter the server and password and it would open up just fine.

Thanks as always for helping!!!  :-)

---

### Post by goemonburo on 2014-01-07
The obvious work around for #5 is to make an ssh tunnel out of the house and back in and use it that way.  I'm sure that would work and that may be the only option.  But it seems silly and totally counter to what VNC is supposed to do.  Plus, it worked fine previously.  Sigh.

---

### Post by steeldriver on 2014-01-07
Sorry I don't know why it isn't working for you - I just tried it using both localhost:3 and 192.168.1.16:3 (the machine's LAN IP) to a vncserver started on display :3 on the same machine by a different user and both worked

---

### Post by goemonburo on 2014-01-07
Well, that's good info right there.  I wonder if it's something not VNC related somehow?  What was the command you used to start it?  Could it be that my screen resolution is somehow not right for the User2 or User3?  Doesn't seem to make sense but...just thinking out loud. 

And do you have a VNC config file somewhere I could look at?

---

### Post by steeldriver on 2014-01-07
First, starting VNC server as a different user - I'm just going to do it via 'su' from an X terminal in my current desktop session [for some reason this seems to inherit the parent session's XAUTHORITY, even when started as a login shell, so I need to export the correct XAUTHORITY - this wouldn't be necessary in general e.g. if I was starting it remotely via an SSH session]

```

otherfella@lap-t61p:~$ su - steeldriver
Password: 

steeldriver@lap-t61p:~$ 
steeldriver@lap-t61p:~$ export XAUTHORITY=$HOME/.Xauthority
steeldriver@lap-t61p:~$ vncserver :3

New 'X' desktop is lap-t61p:3

Starting applications specified in /home/steeldriver/.vnc/xstartup
Log file is /home/steeldriver/.vnc/lap-t61p:3.log

```

Then starting the vncviewer from the original user's desktop

```

otherfella@lap-t61p:~$ vncviewer localhost:3
Connected to RFB server, using protocol version 3.8
Enabling TightVNC protocol extensions
Performing standard VNC authentication
Password: 
Authentication successful
Desktop name "steeldriver's X desktop (lap-t61p:3)"
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using shared memory PutImage
Same machine: preferring raw encoding

```

The ~/.vnc/xstartup file
```

steeldriver@lap-t61p:~$ cat ~/.vnc/xstartup 
#!/bin/sh

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -r "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

gnome-session --session=gnome-classic &

```

---

### Post by goemonburo on 2014-01-07
Interesting, because the big difference is that you used "su" to start it as a different user.  That's a little different than if you started it as "otherfella" while logged in as "otherfella" and then logged out completely and logged in as "steeldriver."

Not that I think it matters.  It shouldn't.  :-)  But it's a bit different than what I was doing.

Also I was typing _xtightvncviewer_ not _vncviewer_.  And I was waiting for it to prompt me for the server location rather than specifying it in the command line.

Anyway...am guessing at this point that maybe I'll need to give up and just ssh outside the LAN and back in.  Haven't tried that yet, if THAT doesn't work then I'll really be baffled...but am betting it will.

Thanks!

---

### Post by steeldriver on 2014-01-07
can confirm it still works for me if I 'switch user' and login to a graphical desktop to start the vncserver, then logout and log back in to the original desktop

---

### Post by goemonburo on 2014-01-08
So interestingly enough, it STILL fails if I ssh out and try to connect while logged in as User2.  Could this maybe be an issue with the port or permissions?!!

---

### Post by steeldriver on 2014-01-08
Are you trying to connect via the WAN IP from inside a LAN? many routers do not support that ('NAT loopback')?

---

### Post by goemonburo on 2014-01-08
I have a dynamic DNS address that I use (if that matters).  But I have no problem sshing out into the world and coming back in on other computers.  I don't think it's the router...but yeeesh, it's a good thought.

At this point I think I'm done.  Might try using your Xstartup file and see if that does something.  I have a funky one because I remember I got a gray screen when I first had VNC...had to monkey around and maybe what's in there is messing it up for some reason?  Just a wild hunch.

Thanks!

---

### Post by steeldriver on 2014-01-08
Yeah thinking about it, if you are getting as far as authentication (being prompted for the VNC password) then it's not a connection or port forwarding issue

---

### Post by goemonburo on 2014-01-25
So turns out that weird things happen when I log into the machine as either User1 or User2 and start VNC.  But what SOLVED all issues is to ssh in from a different computer, no matter who was logged in on the machine locally, and start a VNC session remotely.  

Do that, all works just fine.  And that's not too horrible a work around, since I'm almost always near another machine.  :-)  Thanks for such helpful hints and tips, really appreciated the help along the way!

---

