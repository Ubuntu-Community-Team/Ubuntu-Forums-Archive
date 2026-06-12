---
title: "Stuck after login with weird screen in the middle of desktop 1"
date: 2014-11-02
forum: General Help
---

### Post by cris6 on 2014-11-02
Hello

I have an Acer AO722 (AMD C-60 with 750GB and 4GB RAM) dual boot with Windows "10" tech preview

I am using Ubuntu GNOME 14.10 here with GNOME as default session and some other installed just to test other session managers

And I am having a weird bug here and I could not resolve by myself 

When I restarted Ubuntu 14.10 It showed the login screen with my user name fine, but after I login it shows some crash report stuff and a weird thing:
A "mini" desktop screen at the middle of the main screen "mirroring" stuff at the desktop and nothing works but keyboard and mouse pointer (does not click anything), and I can not click anywhere to close this screen but switching to another session with ALT+F some number. And sometimes it gets so stuck that its even impossible to switch to other views...

So, I tried to resolve this problem by:
I killed gdm and restarted it again and no luck
I even installed AMD proprietary drivers (flrgx-updates) to check if it was some problem regarding GPU and no luck also, so I removed them to test with Ubuntu build-in graphical drivers

And with other session manager the problem still persists, which makes a point that this is not a GNOME issue, but a problem with something from Ubuntu or something installed here that is messing with display and or is blocking the OS to display the real desktop...

I tried KDE Plasma and the system does not display anything but a blank (black) screen with the mouse pointer
I tried LXqt and it behaves like GNOME, but instead of showing the "mini" screen in the middle it only shows system error pop-up and nothing more, since mouse and keyboard are still impossible to use...

Any suggestions about what may be causing this problem and anything to solve this ?

I searched everywhere for this and did not find anything about the reasons that are causing those problems.

TKs !

---

### Post by jhay2 on 2014-11-03
sounds that you are having permission problem .  . maybe try to change your default greeter to a webkit-greeter ,  do not login . switch to another terminal window . then try to login with the terminal . and then start x with root 

"sudo startx"  

if you successfully see the desktop screen , it is more likely a permission problem between the x server (not sudo) and the greeter , 


you might need to change the default greeter , search the google on how to setup a webkit greeter , "sudo apt-get install lightdm-webkit-greeter"

---

### Post by cris6 on 2014-11-03
Hi @jhay2

I did what you told me to but still no luck

GNOME starts the X session but the square in the middle of the screen and the mouse or keyboard not responding to anything but ALT+F to swith to terminal...

Any advice about this square stuff ? Its pretty much weird and I have no idea about what is causing this bug here

tks

---

### Post by buzzingrobot on 2014-11-03
There are a number of kernel options that can be used at boot time that may or may not affect this: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions).  Look especially at the 'nomodeset' option. If that works, it probably will deliver a sub-optimal, but working, display. It would, though, narrow the search to a video issue.

Since you see this on different environments, after a normal and successful login via the display manager, it looks like multiple window managers are unhappy with your hardware.

---

### Post by cris6 on 2014-11-03
Hello
No luck here

I started Ubuntu with nomodeset option and GNOME starts but the square at the middle of the screen is still here, and again, no mouse and no KB input :\

Any ideas ?

tks

---

### Post by buzzingrobot on 2014-11-03
Does "session manage" mean "display manager"?

Each of the different environments you've installed use their own, different, display manager. (Not sure, but I think Gnome insists on using GDM.) In case that's the issue see the section titled, 
"Help, I can't see my Desktop!" in this wiki article: [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM).  It references LightDM, but the procedures are generic. I'd first try resetting the display manager with the dpkg-reconfigure command. (Then reboot, don't just logout, to see if it worked.).

---

### Post by cris6 on 2014-11-03
Hi
Yep, its the display manager
I actually reverted it to GDM to relauch GNOME and the display appears, but it has a "mirror" square in the middle of the screen showing what is in the desktop (mountpoints)
And its impossible to close this square and or other things that are displaying, since mouse and keyboard does not respond.

I am gonna try reusing lightdm to see if it makes other managers make the screen render proper

But do you know what may be causing this weird behavior at all ? Since the screen appears, it should not be something gdm or lightdm related

tks

---

### Post by buzzingrobot on 2014-11-03
I don't have a clue, sorry.  I do have a laptop that sometimes gets its actual DPI (144) used after an install instead of X using 96 DPI.  But, the result there is an oversized display, the opposite of your problem. Plus, you see this in a batch of DE's.

If you can boot into a live session and get a normal display, that would at least confirm the laptop's screen hasn't developed an ill-timed failure.

---

### Post by cris6 on 2014-11-03
Hi
Actually Windows tech preview boots fine, so its not something related to hw failure

Really gonna try booting a live USB from 14.10 to check if I can see what happened or reinstall the OS
Tks

---

### Post by Igni on 2014-11-23
hi,

I upgraded to 14.10 and I am also stuck with the same issue(HP HDX 16T with Nvidia graphics). In empathy window if I hover, it shows buddy information(popup information). Other than that nothing works. The desktop is active but only navigation possible is Ctrl+Alt+F1. The same window(looks like mini-desktop window) shows up in KDE, Gnome, LXDE and Unity desktop environments.

I created a temporary user and the new user also has same issue during first login.

I also have 64 bit Ubuntu in the same laptop(triple boot). I was able to successfully upgrade it to 14.10 without issues. 

Please let us know if there are any specific logs that will help identify such UI issues.

---

### Post by kostas12 on 2014-11-30
I have exactly the same problem cris6. No solution until now. I can' understand what's going on!!
I'm gonna reinstall ubuntu 14.10 right now!

---

### Post by chrissmith-cs on 2015-01-19
I recently had the same problem. I discovered that if after I logged in, I quickly opened the overview, it wouldn't crash, but would still give me the square. It turns out that I had an app (in my case Gnome-do) that caused the problem, and it was set as a startup application. I found the app called Startup Applications (it can also be changed with the tweak tool) and removed it from the list. After that, I restarted the computer, and it worked just fine. If you know which application is causing the problem, uninstalling it should work as well. Hope this helps.

---

