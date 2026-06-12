---
title: "I mysteriously have no ~/.Xresources ubuntu 18.04"
date: 2022-12-05
forum: General Help
---

### Post by david503 on 2022-12-05
Ubuntu 18.04

I'm doing the first step of setting up windows and then 22.04 on my shiny new pc, and the first thing I want to do is set up VNC on my old 18.04 workstation so that I don't have to use two keyboards while I'm looking at my old setup.  

So, I was following this tutorial:

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04)

I skipped the part abou ssh tunneling, so that's not in play.

What I get when I run the server and log into it with gvncviewer localhost:1  is just what you might call "tv static" looking screen- yknow, black and white dots, and I have an X mouse cursor that I can move around.  And that's all.  No menus, nothing. Not what xfce is supposed to look like.

So here's what I figured out. The tutorial says to put this into my ~/.vnc/xstartup file:

#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &

So I looked at what's in the ~/.Xresources file and....

I don't have one.  

Why don't I have one?  

So I guess can someone give me their Xresources guts and tell me what to change in it, if anything?  So that the vnc works?

Weird problem I know.

---

### Post by TheFu on 2022-12-05
> **david503 said:**
> 
So I looked at what's in the ~/.Xresources file and....

I don't have one.  

Why don't I have one?  

So I guess can someone give me their Xresources guts and tell me what to change in it, if anything?  So that the vnc works?

Weird problem I know.

If you don't have one, perhaps you should create it?  I know this is obvious, but I had to be told this decades ago myself.  On Unix, if you need a file and it doesn't exist, create it. Set the owner, group, and permissions to the necessary state/values and move on.  99% of the Linux desktop people in the world don't have any need of a ~/.Xresources file.  I have one on my systems, but it has nothing to do with VNC, so it won't help you at all. In mine, it sets  default fonts for different classes of X/widgets  ... you know like we all did in the 1990s.

BTW, "~/.Xresources" and "Xresources" are two completely different files.  I don't know what the 2nd one is about, but it is just a filename, not something any other programs seek as part of their initialization.  At least, not to my knowledge.  As always, details matter.

---

### Post by david503 on 2022-12-06
> **TheFu said:**
> If you don't have one, perhaps you should create it?  I know this is obvious, but I had to be told this decades ago myself.  On Unix, if you need a file and it doesn't exist, create it. Set the owner, group, and permissions to the necessary state/values and move on.  99% of the Linux desktop people in the world don't have any need of a ~/.Xresources file.  I have one on my systems, but it has nothing to do with VNC, so it won't help you at all. In mine, it sets  default fonts for different classes of X/widgets  ... you know like we all did in the 1990s.

BTW, "~/.Xresources" and "Xresources" are two completely different files.  I don't know what the 2nd one is about, but it is just a filename, not something any other programs seek as part of their initialization.  At least, not to my knowledge.  As always, details matter.

Yea I actually already tried that,

touch ~/.Xresources 

Didn't help.  

What I think is happening is that the reason I get the empty screen is that there are no entries in the Xresources file to tell xfce what it's supposed to look like.  menus, colors, desktop, etc. So without know that it just shows an empty screen with a mouse cursor.

---

### Post by ActionParsnip on 2022-12-06
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

Use the 22.04 guide.

---

### Post by david503 on 2022-12-06
> **ActionParsnip said:**
> [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

Use the 22.04 guide.

Ironically that's where I started.  Then I ran into this problem and switched to the 18.04 guide in attempt to fix it. 

The instructions are the same...  And I wouldn't want to do any of the minor differences because (once again, ironically), using a 22.04 guide on an 18.04 PC seems like asking for even more trouble.

---

### Post by TheFu on 2022-12-06
The gray background means that vnc is showing an empty X root window.  Any X program can be started if the correct DISPLAY environment is setup.  A WM would be a good choice.  If it were me, I'd start fvwm, but I don't use any DE.  Is there a 'startxfce' program on the remote system?  Try running that AFTER setting the DISPLAY correctly.  I'd expect that to be added to the 'startvncserver' script.


But I really know nothing, since we stopped using VNC over a decade ago and use x2go these days when needing a remote desktop from outside the LAN and inside the LAN, we don't use remote desktops much.  'ssh -X' works so much easier to run a program on another system, but have the window displayed on the system I'm sitting at.

---

### Post by david503 on 2022-12-07
> **TheFu said:**
> 

But I really know nothing, since we stopped using VNC over a decade ago and use x2go these days when needing a remote desktop from outside the LAN and inside the LAN, we don't use remote desktops much.  'ssh -X' works so much easier to run a program on another system, but have the window displayed on the system I'm sitting at.

This looks cool but I ran into trouble and the site doesn't have a forum? I couldn't find one...  When I log in all I get a black window for like a half second and then disappears.  

Anyway I guess I should start a seperate post about it- but should I do that here or is there actually an x2go forum somewhere?  

thanks

---

### Post by TheFu on 2022-12-07
Are you trying to use x2go now?

Did you follow the x2go installation guide?  [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go) 

For example, x2go doesn't work with Gnome or KDE, but shoujld work great with XFCE, Mate, or LXQt DEs.  I've used it with fvwm and openbox WMs. It flies in those environments, though 99% of the time on the same LAN, I use 'ssh -X' to run the exact program I want and that program integrates into my current desktop as though it was running locally.

And the NX protocol, which x2go is using requires that ssh be setup.  One of the first things I do on any system here is setup ssh, so I don't know if x2go will install those dependencies or not.  I can't imaging any Unix system without ssh on it, if it is on a network.

Also, there might be issues with x2go and Wayland. IDK.  I can't use Wayland for a number of reasons, so I always use X/11 still.

---

### Post by david503 on 2022-12-07
> **TheFu said:**
> Are you trying to use x2go now?

Did you follow the x2go installation guide?  [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go) 

For example, x2go doesn't work with Gnome or KDE, but shoujld work great with XFCE, Mate, or LXQt DEs.  I've used it with fvwm and openbox WMs. It flies in those environments, though 99% of the time on the same LAN, I use 'ssh -X' to run the exact program I want and that program integrates into my current desktop as though it was running locally.

And the NX protocol, which x2go is using requires that ssh be setup.  One of the first things I do on any system here is setup ssh, so I don't know if x2go will install those dependencies or not.  I can't imaging any Unix system without ssh on it, if it is on a network.

Also, there might be issues with x2go and Wayland. IDK.  I can't use Wayland for a number of reasons, so I always use X/11 still.


Yes I followed the guide (or so I tried), and yes of course I have ssh!  

Woa!  I got XFCE to work!  However this is weird- if I run chrome within the x2go xfce window, it opens it outside the window in my gnome, not within the xfce window.  That's not supposed to happen right.  Ohh maybe it's something like the user I'm running the client as?  Something like that?

---

### Post by david503 on 2022-12-07
Ok here's an update, I was just resizing the x2go session window and it... froze my gnome, I had to drop out of shell and kill it's processes to get back in.  

People really use this?  

And in my defense look at the documentation for the server:

[https://wiki.x2go.org/doku.php/wiki:advanced:x2goserver-in-detail](https://wiki.x2go.org/doku.php/wiki:advanced:x2goserver-in-detail)

It's one page with a bunch of "more text needed here" throughout.  Actually it doesn't even tell you how to start it.   Seriously, look at that page where does it say like "here's how to start the server"....  ug, this is nuts...

The only way I figured out to start it is by running:

sudo /etc/init.d/x2goserver start

Look I appreciate your help, but I'm just gonna go back to getting vnc to run- I'm pretty close now- I switched to x11vnc and it's mostly working.  Again, thanks.  

I'll keep everyone updated now that x11vnc works sort of.

---

### Post by TheFu on 2022-12-07
> **david503 said:**
> Yes I followed the guide (or so I tried), and yes of course I have ssh!  

Woa!  I got XFCE to work!  However this is weird- if I run chrome within the x2go xfce window, it opens it outside the window in my gnome, not within the xfce window.  That's not supposed to happen right.  Ohh maybe it's something like the user I'm running the client as?  Something like that?

I've never used Chrome (and don't plan to ever allow it on any computers here).  Some browsers go out of their way to NOT be run remotely and to seek out a local instance to send commands into.  Since I haven't used MS-Windows much recently, I don't know what the expected behavior is, but I do know that with Chromium and 

For Firefox, I used to provide specific command line options to prevent that behavior before I learned about firejail and the constraints it provides.  I think the option is "--no-remote" or something like that. Check your local manpages for the exact option. It is a FF option, not a firejail option.

Chromium is my "never-let-it-touch-storage" browser, so I run it within a very restricted environment that doesn't let the program touch disk nor see anything on the LAN I specifically don't allow (like DNS).

If you are running x2go on MS-Windows, I vaguely remember that fonts needed to be installed too.  I used to use x2go from Win7 into my Linux desktop for a few years.  That was back when my MS-Windows box was faster than any of my Linux systems - long ago.

MSFT stuff makes things hard.  If you are using Linux for the client(s) and server(s), most things seem to just work and there aren't many compromises.  OTOH, MSFT has their own ideas about how things should work and usually ignores what others did for 5, 10, 20, 30 yrs before. It is very frustrating. They clearly have different agendas than compatibility between other systems.  Nothing you don't already know.  Apple is almost the same, unfortunately.  They seem to rename common protocols so they can copyright and trademark them, even if they've existed for decades first.  Branding gets in the way of real progress.  Sigh.

---

### Post by TheFu on 2022-12-07
> **david503 said:**
> 
The only way I figured out to start it is by running:

sudo /etc/init.d/x2goserver start

The x2go server when a new x2go client request comes in. This is automatic.  In Unix systems, we have this main server (used to be called xinetd) that watches for new connections and if there's a configured system to handle those specific actions, only then does the server to do so get launched.  I vaguely remember that 22.04 systemd was adding this capability back. Some people noticed it with ssh.

It is possible to have 1-500 clients connecting to the same server for x2go without dealing with the DISPLAY like with VNC. It is automatic.  Different people can run their desktop on the remote system and use all the power of shared storage on the same system to work together efficiently.  We've been doing this 30+ yrs, well before webapps attempted it.  

Anyway, maybe you'll come back to x2go later.  Every answer isn't always right for every user, at the time they are ready to use it.  Sometimes more seasoning is needed by the tool or the user before it will fit their needs.  I typically only use x2go from the internet when traveling.  On the LAN, I would run a remote application using 'ssh -X {remote-box} {program} {program options}'.  Actually, I'm running both firefox and thunderbird in that mode now, along with about 15 terminals running on other systems.  Inside those terminals, I can launch almost any program, including GUI programs, and the window for each will show up, fully integrated into the workstation that I'm sitting behind.  Only the window title gives a hint that the program is running on a completely different system.

---

### Post by david503 on 2022-12-07
> **TheFu said:**
> I've never used Chrome (and don't plan to ever allow it on any computers here).  Some browsers go out of their way to NOT be run remotely and to seek out a local instance to send commands into.  Since I haven't used MS-Windows much recently, I don't know what the expected behavior is, but I do know that with Chromium and 

If you are running x2go on MS-Windows, I vaguely remember that fonts needed to be installed too.  I used to use x2go from Win7 into my Linux desktop for a few years.  That was back when my MS-Windows box was faster than any of my Linux systems - long ago.

MSFT stuff makes things hard.  If you are using Linux for the client(s) and server(s), most things seem to just work and there aren't many compromises. 

No, I'm running ubuntu on both client and server in my x2go foray here.  (Hence I said I had to "drop out of shell" and kill it because it froze everything. So... linux.)

I agree about MS and MacOS, hence I'm here in a Ubuntu forum.  The only time I boot into windows (or just run it in virtual) is for (pirated) Adobe stuff.  

thanks, cheers, 

d

---

