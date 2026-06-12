---
title: "VNC or RDP from Ubuntu to Ubuntu problems"
date: 2014-01-30
forum: General Help
---

### Post by kolibri on 2014-01-30
I need to regularly connect remotely from one Ubuntu 13.04 (at the moment) machine to another machine running a near identical ubuntu 13.04 setup.

The only way I could get either RDP or VNC to work was with the script by scaryGliders ([scarygliders.net/x11rdp-o-matic-information/]("http://scarygliders.net/x11rdp-o-matic-information/")), and then using vinagre (remote desktop connection gui) to connect, but it's hit or miss.  Often vinagre will just act like it's connected but only produce a black screen.  I know the other machine is a awake and connected because I can ping it and get a response back.

Remina or other RDP connections claim to be connected but only shown the gray hatchured screen with a large comic X.

Both machines are running Ubuntu 13.04 with gnome fallback and multiple workspaces.

Is there a glitch free way to enable remote desktop/VNC, or at least a way to get any error messages or feedback from either RDP or VNC as to why they won't connect or show the remote desktop?

I wondered if the double workspaces on the remote system was causing a problem, but I can't find a way in vinagre (listed just as remote desktop connection in the applications menu) to automatically pass the user name and password, just incase that dialog box was hidden from me via the second workspace.

thanks.  I never thought RDP from one Ubuntu machine to another would be so difficult.

---

### Post by steeldriver on 2014-01-30
RDP is not a native *nix protocol - I'd suggest sticking with VNC for Ubuntu-Ubuntu

Have you tried the default 'Desktop Sharing' option (based on vino-server)?

---

### Post by kolibri on 2014-01-30
> **steeldriver said:**
> RDP is not a native *nix protocol - I'd suggest sticking with VNC for Ubuntu-Ubuntu

Have you tried the default 'Desktop Sharing' option (based on vino-server)?

I guess I've only been succesful using RDP to get remotely from one of our Windows lab machines to my Ubuntu Desktop.

Anytime I've connected Ubuntu to Ubuntu it's been with VNC.

I first used the default Desktop sharing dialog box in the applications menu to set up desktop sharing.  But I couldn't get Remmina or Remote desktop viewer (Using VNC) to connect until I let the scaryglider script make the changes it implements.  But even after the Scaryglider install, connecting through VNC is a crapshoot, and I can't even tell why it fails and just gives me a black screen.

---

### Post by kolibri on 2014-02-01
Bumped because my cats like it when I work at home!

---

### Post by ian-weisser on 2014-02-01
Are you trying to log in to a new remote session?
Or are you trying to see an existing remote session?

---

### Post by kolibri on 2014-02-01
> **ian-weisser said:**
> Are you trying to log in to a new remote session?
Or are you trying to see an existing remote session?

I'm trying to log into a new session.  Right now I'm back at work and  trying to see if something is turning off the VNC server settings  somehow, saw some posts about those kinds of problems.

I've got vino-server running, and 6 Xvnc processes running (looking in system monitor), and yet I couldn't connect to anything but a black screen when trying to connect to this machine.

---

### Post by ian-weisser on 2014-02-01
The VNC server may be running...but the X server probably is not.
The X server starts upon user login...and you're not logged in yet.

It's a classic chicken-and-egg problem.
One way is to connect using SSH and start X manually. Then VNC can attach to the running session.
Lightdm (Ubuntu 13.04+) also has a feature for logging into remote systems that includes starting X.

---

