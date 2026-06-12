---
title: "How to make screen sharing more responsive?"
date: 2019-01-29
forum: General Help
---

### Post by donb21 on 2019-01-29
I have a new installation of 18.04 and setup screen sharing, using the RealVNC client on a Win7 box to access Ubuntu.  It generally works, but  tends to be really sluggish.  If  I open a terminal, typed letters don't show up on the remote end very quickly.  Sometimes I hit Enter and nothing happens, then hit Enter again and I get two carriage returns on the remote end.  It's as if the server is waiting for something.  Did I miss something in the setup?

PS - This is a home network, all on the same segment.  The Ubuntu and Win7 boxes are 10 feet apart with two gigabit switches in between.

---

### Post by TheFu on 2019-01-29
a) don't use a DE that wants direct GPU access.  That means you can't/shouldn't use Gnome3 or Unity or KDE for a remote desktop.  This applies reguardless of the VNC, RDP or NX tool used.   Acceptable performance is possible from Mate, XFCE, LXDE desktops or using plan Openbox or plan Fvwm-Crystal window managers.  A DE is not a requirement.

b) Use ssh for 95% of the stuff you need linux for, not a GUI.

c) NX protocol feels 2-3x faster than VNC or RDP. **x2go** is the easiest NX tool to get working and has the added benefit that since all connectivity is through an ssh tunnel, it is considered secure over the internet, assuming you don't use passwords.  I use x2go from Windows7 to a virtual machine desktop daily, constantly. Also from Linux desktops. It is very stable with both .... like over 30 days between app restarts, stable.

d) If the client is Linux/Unix with an X/Server, then you can use the built-in X11 protocol to have applications running on a different machine, but displayed on your local machine. I haven't used an X-server on Windows that was good since some commercial offerings in the early 2000s.  The free versions were always very buggy back then. Setting up X/Windows to work easily on Windows has always been a hassle and difficult for non-experts.

In short, use x2go and be happy with better performance and better security.  No solution will let you watch videos, however, so if that is your hope forgetaboutit.

The trick to make x2go easy to setup is to get ssh working first, then add the x2go PPA onto both the client and the server, then install the client on the client and the server on the server.  For Windows clients, be certain to install the huge font package just to make your life easier.  Also, mark a reoccurring reminder on your calendar to update x2go on Windows every quarter.  That's the main reason I stopped using Windows much - too hard to maintain all the software.

Anyways, if you still want to use VNC, be certain to set a 30+ character password, since VNC hacking is constant and use one of the lite DEs.

---

### Post by HermanAB on 2019-01-30
A terminal?  Don't use screen sharing for a terminal.  Use SSH.  Even Windows nowadays comes with SSH and if you have an old version of Windows, use Cygwin or PuTTY.

---

### Post by kashioz on 2019-01-30
Check Ubuntu Documentations.


Open the Activities overview and start typing Settings.


Click on Settings.


Click on Sharing in the sidebar to open the panel.


If Sharing is OFF, switch it to ON.


If the text below Computer Name allows you to edit it, you can change the name your computer displays on the network.


Select Screen Sharing.


To let others view your desktop, switch Screen Sharing to ON. This means that other people will be able to attempt to connect to your computer and view what’s on your screen.


To let others interact with your desktop, switch Allow Remote Control to ON. This may allow the other person to move your mouse, run applications, and browse files on your computer, depending on the security settings which you are currently using.

---

### Post by donb21 on 2019-01-30
I already have screen sharing enabled and working, but it doesn't work very well.  It's OK if the remote is a little slow, but this is almost unusable.  Sometimes the host computer screen changes completely and the remote doesn't update until I enter some other keystroke...not good.  I also use Putty on port 22 for anything CLI, which works fine, but some things require a GUI, so, here I am.

Are we saying that screen sharing doesn't work with the default desktop?  I'll try a different DE if that's the answer, but it strikes me a bit odd that they would package it that way.

---

### Post by TheFu on 2019-01-30
> **donb21 said:**
> Are we saying that screen sharing doesn't work with the default desktop?  I'll try a different DE if that's the answer, but it strikes me a bit odd that they would package it that way.

Yep. That is the answer. I'd say use **Mate DE**, but any of the Gnome2-based DEs should be fine/lite.  It shouldn't badly interact with Gnome3.  In Unix, the GUI is just another program. It isn't tightly integrated into the OS any more than a little calculator app is.  This means that swapping out a DE isn't that big of a deal.  It also means that many different 3rd party apps can do things impossible if only 1 desktop was available.  And it is why 1 computer can be concurrently shared by 20-100 students, all running desktops (X/servers) on minimal hardware.  Flexibility is the main feature for Unix systems because anyone can take a few smaller tools and make something amazing that fits their needs.

But **[B]on the same LAN**[/B], most people would use X/Windows client/server to run applications on other systems, but display the window locally.  That is the Unix way.  VNC is a hack needed to support Windows users, at least before NX was stable.  NX is a hack too, BTW, but it is more efficient in bandwidth and actually has _some_ security.

Didn't you hear? This is the year of of the Linux desktop. ;)

IMHO.

---

### Post by donb21 on 2019-02-03
Apparently, that is the answer.  I tried Ubuntu-Mate, with the remote desktop package from nomachine.  It works really well; the host and remote displays track with very little delay.  Thanks for the advice, this looks like a much better way to go.

Don

---

### Post by TheFu on 2019-02-03
> **donb21 said:**
> Apparently, that is the answer.  I tried Ubuntu-Mate, with the remote desktop package from nomachine.  It works really well; the host and remote displays track with very little delay.  Thanks for the advice, this looks like a much better way to go.

Don

NoMachine is a proprietary implementation of the NX protocol with limitations.  x2go is one of the non-proprietary implementations, none have those limitations.  Just something to consider.

But if it is working for your needs, I wouldn't change at this point.

Please mark the thread as solved - **Thread Tools button** near the top. It helps the community.

---

### Post by 1clue on 2019-02-03
+1 for a different window manager, preferably without a desktop.
+2 for ssh only.

Not sure what you're doing, not sure I need to know. But there is nothing at all that a Linux server needs to do which requires a GUI.

If your Ubuntu box is your home workstation and you want to get at it from work, or vice versa, then you may want to continue with the GUI. If you intend the remote box to be a server, then I recommend that you learn how to use the command line for whatever you think you need the GUI for. Or maybe use one of the web-based configuration tools.

The description of window managers above is accurate in that some want direct hardware access and others don't. There are lots of window managers, new and old, active and inactive. Some of the old ones like FVWM have been around for decades and still have a significant following.

More to the point, there are window managers which were designed specifically to be used across the network for remote GUI login sessions, and others which were designed to be minimalist and thus work fairly well on remote connections. Keep in mind that the client/server role for X11 is reversed from what is intuitive. The X SERVER is where you are typing and where the windows show up, which is always where the user is sitting. The X CLIENT is where your application is running, which can be where the user is sitting but can also be on the other side of the Internet.

Also keep in mind that encryption takes a toll, and you may or may not want to pay it. Using ssh makes the gui easier to get working, but ssh has encryption built-in. Encryption means you're sending more bytes of data for the same number of keystrokes. Or, more bytes of data to represent a screen on a remote box. So by that measure if you have lots of animations and widgets they will slow your system down. 

The other side of encryption is that if you're going unencrypted across an insecure network, spectators may see your network traffic and get information about you that you would rather not share.

---

### Post by donb21 on 2019-02-03
I'm using it for Mythtv (HDPC) and a basic file server.  The box is connected directly to a TV, which is often in use, so remote access is pretty useful.  Once it's setup and configured, it mostly hands-off, but I still need to do occasional  maintenance work.  Kicking the family off the TV is not so easy.  Most of the setup screens are GUI-based and have lots of smarts built in, so it's  usually pretty dicey to edit things directly.

Don

---

### Post by 1clue on 2019-02-03
While I don't use MythTV or any of that, I'd be amazed if there is not also a web interface or some other way to check configuration before saving.

---

### Post by 1clue on 2019-02-03
As far as file sharing is concerned, I'm 100% positive you can do that without a GUI. Pretty sure samba has a built-in web server config screen. It might not be turned on, but this is pure server software, meaning you do not need a gui.

I'd lay pretty good money on MythTV having a command line configuration too.

You might want to investigate curses-based apps for these, if they don't have web front-ends.

---

