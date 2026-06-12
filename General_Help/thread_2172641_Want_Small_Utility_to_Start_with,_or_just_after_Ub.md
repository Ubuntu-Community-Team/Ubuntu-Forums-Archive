---
title: "Want Small Utility to Start with, or just after Ubuntu"
date: 2013-09-05
forum: General Help
---

### Post by dyers2 on 2013-09-05
I am very new to Ubuntu, so I may be missing something very obvious.  I've read a dozen or more solutions to this issue, but I haven't found one that solves it for me yet. I'm using Ubuntu Studio 13.04 (Xfce desktop). Many have advised locating Startup Applications in the Dash menu, but it's no longer included in that menu. I've used both Catfish File Search, and Application Finder to search for Startup, and I've manually searched the main menu editor; not to be found. A couple of the posts I read suggested to open Dash, and type Startup Applications there, but there's no fields in which to type that I can see.  Someone else pointed to an icon on the far right that looks like a gear, but I don't see that either.

A number of people suggested doing something like this:> sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop A few more people suggested adding the program to the autostart directory using something like this: > sudo ln -s /usr/share/applications/filename.desktop /etc/xdg/autostart/.  The application I wanted to add to Autostart was added, but when I reboot, that utility didn't start. I'll appreciate very much any ideas.

[SIZE=4]&#9774;[/SIZE]  Dave

---

### Post by Bucky Ball on 2013-09-05
A/ Xfce doesn't use Dash, that is a Unity DE thing;
B/ Apps>Settings>Settings Manager>Session & Startup.

Just 'Add' what you want to start at boot there.

You seem to be on a bit of a (possibly unessecary) wild goose chase and it would help if you stated what you want to start at boot (unless I'm missing that in your post). Dash instructions don't apply to Xfce. Good luck. ;)

---

### Post by dyers2 on 2013-09-05
Hi, Mr. Fuller!

Thanks for your response. I appreciate the clarification on Dash. As much time as I spend in Settings Manager, I don't remember giving Session and Startup much more than a glance, or two. There are now 2 applications I want to start when Ubuntu boots. The first is CheckGMail. I funnel my 3 email accounts through that one, and this widget lets me know when there is email, and even lets me read the first few lines. The other is VLC. I use it to stream our local NPR/Jazz station.

I made several attempts to add both utilities, but it still doesn't work. It's the commands; I don't know how to write them.

[SIZE=4]&#9774;[/SIZE]  Dave

---

### Post by Bucky Ball on 2013-09-06
Open a terminal and:

vlc

That will open vlc. Should be all you need in Session & Startup.

As for checkgmail, never used, but open a terminal and try 'checkgmail' (or whatever the actual widget is called) and see if that launches it. Whatever launches it from a terminal should be all you need in Sessions & Startup. Should be ... ;)

PS: And a 'hi' to you, but I am not the celebrated Mr Fuller, merely one of the balls named in his honour! ;)

---

### Post by Bucky Ball on 2013-09-06
Open a terminal and:

vlc

That will open vlc. Should be all you need.

As for checkgmail, open a terminal and try just: checkgmail (or whatever the actual widget is called) and see if that launches it. Whatever launches it from a terminal should be all you need in the Sessions & Startup. Hopefully. ;)

---

### Post by dyers2 on 2013-09-06
Excellent; that did it. Curiously, however, the vlc command in terminal output many hundreds of errors like this:

> [0xb4f1d9c8] xml xml reader error: XML parser error (line 283) : No declaration for attribute id of element Image
[0xb4f1d9c8] xml xml reader error: XML parser error (line 283) : No declaration for attribute x of element Image
[0xb4f1d9c8] xml xml reader error: XML parser error (line 283) : No declaration for attribute image of element Image
[0xb4f1d9c8] xml xml reader error: XML parser error (line 283) : No declaration for attribute lefttop of element Image
[0xb4f1d9c8] xml xml reader error: XML parser error (line 283) : No declaration for attribute rightbottom of element Image
[0xb4f1d9c8] xml xml reader error: XML parser error (line 283) : No declaration for element Image
[0xb4f1d9c8] xml xml reader error: XML parser error (line 284) : No declaration for attribute id of element Image

These errors are in "theme.xml", a file that was "created using the VLC Skin Editor 0.7 (http://www.videolan.org/vlc/skineditor.php)". Lines 283, & 284 are:

> 283      <Image id="trf_vid" x="300" image="vid_trf" lefttop="righttop" rightbottom="rightbottom"/>
284      <Image id="lf_vid" y="35" image="vid_lf" rightbottom="leftbottom"/>

With that, the theme seems to be working visually as it should, and the player works flawlessly. Is this anything about which to be concerned? There is another question: when I open VLC through the main menu, or now when I boot Ubuntu, it stays open until I close it. However, when I use the command vlc to open it, it closes when I close Terminal. Is that expected behavior?

[SIZE=4]&#9774;[/SIZE] Dave

PS; I'm a fan of his geodesic dome.

---

### Post by Bucky Ball on 2013-09-06
> **dyers2 said:**
> 


With that, the theme seems to be working visually as it should, and the player works flawlessly. Is this anything about which to be concerned? There is another question: when I open VLC through the main menu, or now when I boot Ubuntu, it stays open until I close it. However, when I use the command vlc to open it, it closes when I close Terminal. Is that expected behavior?

Totally expected. As it should be. 

As for the errors its throwing in a terminal, ah, wouldn't worry if it's working. If it wasn't they would definitely be a handy clue as to what's going wrong. If you have probs with an app, that is exactly what you should do to dig a bit deeper; run in a terminal and see what it throws. Most apps open simply with their name. Give it a try. If it doesn't, it will open in a terminal with something and that something is usually easily findable on the interwebs. Search 'open in terminal <program_name>'. 

checkgmail working okay too? If so, and issue solved to your satisfaction, please mark as solved from Thread Tools at top right to help others . ;)

---

