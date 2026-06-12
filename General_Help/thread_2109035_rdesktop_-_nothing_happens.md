---
title: "rdesktop - nothing happens"
date: 2013-01-26
forum: General Help
---

### Post by Rocket J Squirrel on 2013-01-26
Lubuntu (Ubuntu 12.04).

I installed rdesktop using Synaptic Package Manager. It completed without error. There is no entry for rdesktop on any of the startup menus. rdesktop itself is in /usr/bin but when launched either by the startup menu's "Run" line, or from File Manager, nothing happens. If I try to run it from Terminal, I get:

> jack@jack-Aspire-one:/usr/bin$ rdesktop
rdesktop: A Remote Desktop Protocol client.
Version 1.7.0. Copyright (C) 1999-2011 Matthew Chapman et al.
See [http://www.rdesktop.org/](http://www.rdesktop.org/) for more information.

Usage: rdesktop [options] server[:port]
   -u: user name
   -d: domain
   -s: shell
   -c: working directory
   -p: password (- to prompt)
   -n: client hostname
   -k: keyboard layout on server (en-us, de, sv, etc.)
   -g: desktop geometry (WxH)
   -f: full-screen mode
   -b: force bitmap updates
   -L: local codepage
   -A: enable SeamlessRDP mode
   -B: use BackingStore of X-server (if available)
   -e: disable encryption (French TS)
   -E: disable encryption from client to server
   -m: do not send motion events
   -C: use private colour map
   -D: hide window manager decorations
   -K: keep window manager key bindings
   -S: caption button size (single application mode)
   -T: window title
   -N: enable numlock syncronization
   -X: embed into another window with a given id.
   -a: connection colour depth
   -z: enable rdp compression
   -x: RDP5 experience (m[odem 28.8], b[roadband], l[an] or hex nr.)
   -P: use persistent bitmap caching
   -r: enable specified device redirection (this flag can be repeated)
         '-r comport:COM1=/dev/ttyS0': enable serial redirection of /dev/ttyS0 to COM1
             or      COM1=/dev/ttyS0,COM2=/dev/ttyS1
         '-r disk:floppy=/mnt/floppy': enable redirection of /mnt/floppy to 'floppy' share
             or   'floppy=/mnt/floppy,cdrom=/mnt/cdrom'
         '-r clientname=<client name>': Set the client name displayed
             for redirected disks
         '-r lptport:LPT1=/dev/lp0': enable parallel redirection of /dev/lp0 to LPT1
             or      LPT1=/dev/lp0,LPT2=/dev/lp1
         '-r printer:mydeskjet': enable printer redirection
             or      mydeskjet="HP LaserJet IIIP" to enter server driver as well
         '-r sound:[local[:driver[:device]]|off|remote]': enable sound redirection
                     remote would leave sound on server
                     available drivers for 'local':
                     alsa:	ALSA output driver, default device: default
         '-r clipboard:[off|PRIMARYCLIPBOARD|CLIPBOARD]': enable clipboard
                      redirection.
                      'PRIMARYCLIPBOARD' looks at both PRIMARY and CLIPBOARD
                      when sending data to server.
                      'CLIPBOARD' looks at only CLIPBOARD.
   -0: attach to console
   -4: use RDP version 4
   -5: use RDP version 5 (default)

This isn't very helpful. I'd like to launch it from one of the start menus.

---

### Post by cwsnyder on 2013-01-26
rdesktop isn't meant to launch from _your_ desktop, it is meant for a remote computer logging in to your desktop.

---

### Post by sudodus on 2013-01-26
It works like this:

You install and run a server on one computer with for example the following ip-address: 192.168.0.2

```
sudo apt-get install xrdp
```

Then you connect the client rdesktop with the following command
```
rdesktop 192.168.0.2
```
from another computer.

I use ***remmina*** for this purpose. Try both alternatives :-)

*Edit*: rdp is also available in Windows. Also put a code box around the rdesktop command to make it easier to see

---

### Post by Rocket J Squirrel on 2013-01-26
Oh, I guess I got confused. The description of rdesktop provided by Synaptic is:

> rdesktop is an open source _client_ for Windows NT/2000 Terminal Server, capable of natively speaking its Remote Desktop Protocol (RDP) in order to present the user's NT/2000 desktop.

(Underline mine)

I have win's Remote Desktop server running a Windows 7 machine, and I need a client to view its desktop using my Ubuntu machine.

---

### Post by sudodus on 2013-01-26
> **Rocket J Squirrel said:**
> Oh, I guess I got confused. The description of rdesktop provided by Synaptic is:



(Underline mine)

I have win's Remote Desktop server running a Windows 7 machine, and I need a client to view its desktop using my Ubuntu machine.

Maybe I was not clear enough in the previous post.

You are right, rdesktop is the client, and you run it in Ubuntu with the command
```
rdesktop ip-address
``` for example
```
rdesktop 192.168.0.2
``` if 192.168.0.2 is the ip address of the server computer (in your case the Windows 7 computer).

---

### Post by sudodus on 2013-01-26
I tested rdesktop, and it runs at least as well as remmina in my computer at this moment, maybe not very customizable while running, but it's doing its job well.

I use the -g option to get the desired remote screen size, for example

```
rdesktop -g 1024x768 192.168.0.2
```
```
rdesktop -g 1600x900 192.168.0.3
```

---

### Post by Rocket J Squirrel on 2013-01-26
Sudodus: thank you for the clarification on using rdesktop. Works just fine. 

I'm looking for a gui front-end to run in LXDE. 

Thanks for the suggestion to use Remmina. Alas, it hangs in both RDP and VNC viewing sessions. 

grdesktop doesn't seem to provide full-screen use nor is there anything but two pages in the Help. 

gnome-rdp seems buggy: it won't save session setting, isn't letting me edit the Properties of a session. 

vinagre seems to be working alright, but when in full-screen mode, I can't access the server's (win 7) pop-up toolbar at the bottom of the screen. Have to exit full screen and scroll to the bottom of the window to do that. 

So far, then the search for a gui continues. Suggestions are welcome.

---

### Post by sudodus on 2013-01-26
> **Rocket J Squirrel said:**
> Sudodus: thank you for the clarification on using rdesktop. Works just fine. 

I'm looking for a gui front-end to run in LXDE. 
...
What do you mean by gui front-end? I hope rdesktop is showing a graphic remote screen for you. Do you mean a window to set the preferences?

If rdesktop is the most stable client, I suggest that you find command line options and use them in the future. You can make an alias for it to launch quickly from a terminal window. Enter the following line (or something similar suitable for ***your*** application) into [FONT="Courier New"][SIZE="3"].bashrc[/SIZE][/FONT]
```
alias rd3='rdesktop -g 1600x900 192.168.0.3'

```
After log out and log in, you will start a remote session with the simple command
```
rd3
```

---

### Post by Rocket J Squirrel on 2013-01-26
The monitor here on my cheapo Aspire One netbook is 1024x600.

To use rdesktop to view the full screen of the Win 7 RDP server, which is 1360x768 I use

> rdesktop -g 1024x600 192.168.1.2 (example IP address)

and everything fits on the screen here. But I cannot access the server's Win 7 toolbar at the bottom of its screen. Lubuntu's toolbar pops up instead. 

But if I launch rdesktop in fullscreen mode:

> rdesktop -f 192.168.1.2 (example IP address)

Then I can get to the server's toolbar. Exiting rdesktop's fullscreen mode is crtl-alt-enter

So far, then, rdesktop is giving me the best results. If I can't find a gui that works here, I reckon I have to write some scripts to launch rdesktop depending on which server I want to contact.

---

### Post by Rocket J Squirrel on 2013-01-26
"What do you mean by gui front-end?"

I mean a non-CLI front-end for rdesktop to set up and save sessions settings, etc., to make launching an RDP session easier for people uncomfortable with the CLI.

---

### Post by sudodus on 2013-01-26
> **Rocket J Squirrel said:**
> The monitor here on my cheapo Aspire One netbook is 1024x600.

To use rdesktop to view the full screen of the Win 7 RDP server, which is 1360x768 I use



and everything fits on the screen here. But I cannot access the server's Win 7 toolbar at the bottom of its screen. Lubuntu's toolbar pops up instead. 

But if I launch rdesktop in fullscreen mode:



Then I can get to the server's toolbar. Exiting rdesktop's fullscreen mode is crtl-alt-enter

So far, then, rdesktop is giving me the best results. If I can't find a gui that works here, I reckon I have to write some scripts to launch rdesktop depending on which server I want to contact.

Please post the code between code tags like this
[noparse]```
output
```[/noparse]
to get output like this
```
output
```
instead of quote tags
[noparse]> output[/noparse]
Code tags survive quoting.
--
I see, and agree how to avoid hiding the bottom of the remote screen. I was doing it the other way around, sitting at a 1920x1080 screen looking at a fairly old laptop, which will be slow with such high resolution.

Anyway I suggest aliases to make it convenient, for example
```
alias rd3='rdesktop -f 192.168.1.3'
```

---

### Post by sudodus on 2013-01-26
> **Rocket J Squirrel said:**
> "What do you mean by gui front-end?"

I mean a non-CLI front-end for rdesktop to set up and save sessions settings, etc., to make launching an RDP session easier for people uncomfortable with the CLI.

Quite similar to the reason to make remmina:
[[COLOR="Red"]http://remmina.sourceforge.net/faq.shtml[/COLOR]]("http://remmina.sourceforge.net/faq.shtml")
> FAQ - Background

Q: Why did you start this project?
    A: The whole story started from my new netbook Eee PC. I bought it and installed Debian on it. I really enjoyed it until I realized that the default installation of the RDP client 'tsclient' on Debian is quite annoying for me:

        The Eee PC has very small screen resolution, but it won't allow me to scroll when I am connecting to my desktop. I can move the window by pressing Alt, but I have to disable capturing all WM key bindings, and it means no Alt-Tab in remote desktop. This made me crazy.
        In fullscreen mode, it occupies all my virtual desktops and provides no control. I can do nothing else when I am connecting to my desktop. When I roll my desktop cube, RDP is in all sides.
        I had great experience with Krdc, which is part of the KDE project. But in order to install Krdc in Gnome desktop, I have to install tons of additional dependencies; This is obvious not a good news for a small netbook user, or a Gnome fan.
        Remote desktop is one of the most frequently used application to me in my netbook; I have to look for a perfect solution.

    Well, if you happen to be in the same boat as me, I hope this is the place you are looking for! 
Q: Why the name "Remmina"?
    A: This is mostly personal preference. :) But just for you to easier remember it, it can also stand for Remote Mini Assistant. 

Maybe you can co-operate in some of the available projects, remmina or another one, so that you don't have to start from the beginning.

---

### Post by Rocket J Squirrel on 2013-01-26
Sorry about the "code" thing. 

Remmina, as I posted above, isn't working for me. It hangs on both RDP and VNC sessions. 

Thank you for the suggestion for the alias. I put the following into ~/.bashrc:

```
# My aliases for running programs from the CLI
# Run RDP on the LAN to view J's computer

alias rd3='rdesktop -f 192.168.1.115:3389'
```

Then I logged out and logged back in. Into Lubuntu's "Run" field I entered

```
rd3
```

and received this:

```
Failed to execute child process "rd3" (No such file or directory)
```

I realize that this thread is drifting at this point.

---

### Post by sudodus on 2013-01-26
> **Rocket J Squirrel said:**
> Remmina, as I posted above, isn't working for me. It hangs on both RDP and VNC sessions. 

I need to set a reasonable screen size, and maybe also reasonable video quality (I don't remember, did the basic config long ago). But I think you can get remmina working with some tweaking.
> 
Thank you for the suggestion for the alias. I put the following into ~/.bashrc:

```
# My aliases for running programs from the CLI
# Run RDP on the LAN to view J's computer

alias rd3='rdesktop -f 192.168.1.115:3389'
```

Then I logged out and logged back in. Into Lubuntu's "Run" field I entered

```
rd3
```

and received this:

```
Failed to execute child process "rd3" (No such file or directory)
```

I realize that this thread is drifting at this point.
Aliases work in text screens and terminal windows, but not in the 'Run field'.

This is no problem for me, because I normally have at least one terminal window open. I enjoy the great flexibility and power of the command line interface.

---

### Post by Rocket J Squirrel on 2013-01-26
"Aliases work in text screens and terminal windows, but not in the 'Run field'."

Sheesh. I'm always the last to hear about things. Yep, the alias works just find in a Terminal window. I suppose there's a good reason that aliases don't work in the "run" field. 

I keep a terminal window open all the time, too, but I'm looking to set things up for my wife, make things easier. Plus having a GUI launcher for RDP in one of the startup menus would reduce the odds that I will forget about this alias the next time I need it, since a good front end should remember session settings, etc. 

I'll continue to hammer at remmina.

Many thanks for your help.

---

