---
title: "VNC Server won't accept mouse clicks, keyboard input"
date: 2007-10-24
forum: General Help
---

### Post by JohnSka7 on 2007-10-24
Hello all,

i just finished installing Gutsy Server and everything seems to have gone fine except for a few web/mysql related things. I was trying to VNC into my headless server to make the updates when I noticed that the machine no longer will accept keyboard input or mouse clicks. I can move the mouse, and when I hover over icons they light up, but nothing if I click, double click, right click or hit any keys.

So I did a bit of research and I figured that my remote desktop preferences might have been reset. What I'm trying to figure out now is, can I set my prefs to "Allow other users to control your desktop" to true without having to hook up a monitor/keyboard to do so? Can I command-line enter this value?

Thanks!

---

### Post by brundles on 2007-10-31
Seeing a similar problem on a friends PC that has just had Gutsy installed on it. Killing the VNC session and manually restarting it seems to clear it for a while but then it reverts back to ignoring keyboard input and mouse clicks.

I'm pretty sure any fix is going to involve needing direct access again for a short period but haven't yet worked out what it's doing and what will resolve it. The trigger seems to be a period of inactivity - I was connected for ages doing stuff to it last night but now it barfs after a short period.

I can't get access to the machine at the moment to try it on his setup, but if you have access to yours you could try logging in normally as the user with VNC and checking the screensaver/locking options - that could be something to do with it.

---

### Post by ryanc on 2007-11-29
Has anyone found a solution to this issue? I am in the exact same situation after upgrading my server from fiesty to gutsy. Vnc worked great before but now it does not accept mouse clicks (however keyboard input appears to be accepted). I am using Xvnc launched from the command line.

---

### Post by brundles on 2007-11-30
I did find that removing all power saving & screen saver options resolved this - not sure if it's idea for your situation though.

---

### Post by crazybilly on 2007-12-04
I'm having the same problem on Dapper.  I'll give the screensaver/power options stuff a try.

Is there any way to restart an X session from ssh?

---

