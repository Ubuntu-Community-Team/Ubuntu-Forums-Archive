---
title: "Problem with Thunderbird Message Filter drop down menus not selectable"
date: 2021-07-30
forum: General Help
---

### Post by FoxJT on 2021-07-30
Firstly, apologies if this is not the right place / inappropriate to post this here.

My system: Ubuntu V:20.04 / Thunderbird V:78.11.0

I use Thunderbird as my email client on Ubuntu and the problem is/seems to be specific to Thunderbird. Thunderbird uses message filters which have drop down menus to select options.  Until recently, they all worked OK and the options were selectable. Now, I can still open the filters but none of the options are selectable. Could that be a "problem" with Thunderbird's interface with the GUI?  I don't see it with anything else. 

The problem may have been introduced in a recent software update(?). Is there a log which shows recent updates info?

I have asked the same question on the Thunderbird Forum.

As I said, apologies if this is the wrong place to ask this question.  Thank you.

---

### Post by TheFu on 2021-07-30
I'm running thunderbird 78.11.0 (64-bit) on 20.04 and haven't noticed any issues. 

Actually, the Thunderbird team did something in the last release that drastically made the entire GUI faster. Last week, opening any menu would take 15-25 seconds. Now it is nearly instant.  
For security, I run TB on a remote system, using X-Forwarding via ssh and inside a firejail sandbox.  My local system runs X11 on 18.04 with fvwm as the WM.

The script I use to start thunderbird is this:
```
#!/bin/bash
ssh -X thefu@regulus "/usr/bin/firejail /usr/bin/thunderbird  " &
```

I use firejail for all high-risk programs like thunderbird and all web browsers.   For running it local (on the same machine we are sitting behind), use
```
#!/bin/bash
/usr/bin/firejail /usr/bin/thunderbird &
```
to be safer.  

If you don't have firejail, it can be installed along with supporting profiles using:
```
sudo apt install firejail firejail-profiles 
```
If you'd like a GUI, there's a package called firetools. I've never used it.  May want to use the firejail PPA to get the latest versions. On 20.04, I haven't needed that.  On 18.04, it is definitely required or some browsers will fail to run at all. I don't think TB was as picky.

---

### Post by FoxJT on 2021-10-15
I have reported this problem on Bugzilla but no solution yet.

---

### Post by FoxJT on 2022-07-24
System: UBUNTU 22.04 (LTS), Gnome: 42.2, Tbird: 91.11.0 (64 bit), Wondow system: Wayland.

Update to what I am seeing.  I now can select any menu item and, if I wanted to, I can move away to another item as expected.  The only thing now is that if I pause on an item that has a sub menu attached, that sub menu is opened and I can select any item in the sub menu. However, if the menu item I paused on wasn't the one I wanted, I then can't select any other menu item in my original menu. It is like an "automatic" selection rather than a mouse click selection.
I then have to close the Message Filters window and start again.  Still annoying but it does almost work correctly!

---

