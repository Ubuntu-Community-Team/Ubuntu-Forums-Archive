---
title: "Copy text from PuTTY window"
date: 2014-01-16
forum: General Help
---

### Post by lz1dsb on 2014-01-16
I'm a bit confused with PuTTY...
How can I copy a text from PuTTY window, and paste it in a simple text file? I'm confused... Selecting the text and than Shift+Ins works, but only within the PuTTY session! When I try to paste the content in a simple text file, it doesn't.
It's quite frustrating as for any terminal application out there this is probably the on of the very basic functions it should support. Am I missing some configuration here?

---

### Post by TheFu on 2014-01-16
Putty ... on MS-Windows?

---

### Post by silvervulpus on 2014-01-16
you might consider maybe using screenshot, then retyping it, or maybe go download leafpad, gedit, or abiword and redo your putty projects on leafpad, gedit, or abiword...

---

### Post by silvervulpus on 2014-01-16
also know that control+c and control+v never work in terminal, they have different uses there... right click copy right click paste is the only copypasta method available for terminal, atleast in ubuntu 12.4

---

### Post by llamabr on 2014-01-16
> **TheFu said:**
> Putty ... on MS-Windows?
Seems almost any other forum would be a good place to ask that question. Doesn't seem related to Ubuntu in any way.

I use putty all the time -- to log into my ubuntu server, when I'm at the office, or another public computer running some other OS.  So rather than try to show off, I'll just answer the question.

Putty (or maybe windows -- I don't claim to understand the magic of it) automatically copies whatever you highlight into the clipboard.  So you simply highlight something with your mouse, it gets magically copied, and then you can paste in the normal way, by right clicking, or ctrl-v.

Welcome to the forum.  It's a generally friendly place.

---

### Post by bertan2 on 2014-01-16
Right click on the bar at the top of the window and select **Copy All to Clipboard**.

---

### Post by mcduck on 2014-01-17
> **silvervulpus said:**
> also know that control+c and control+v never work in terminal, they have different uses there... right click copy right click paste is the only copypasta method available for terminal, atleast in ubuntu 12.4
Shift-Ctrl-C & Shift-Ctrl-V works, as does the [primary selection]("http://en.wikipedia.org/wiki/X_Window_selection") (highlight text to copy, middle-click to paste).

What comes to PuTTY, the copy methods (like many other things) depend on the settings you are using, as PuTTY is able to emulate various different behaviours from different operating systems and terminal emulators.

---

### Post by lz1dsb on 2014-01-17
It does not work for me... I select something from the console and than there's nothing copied in the clipboard. I also don't have the option** Copy all to clipboard **when I select windows menu. And yes, we're talking about PuTTY for Linux. 
Again, selecting the text from PuTTY and than Shift+Ins works, but only within the same PuTTY window. I cannot translate that to another application. I also notice today that this behavior is probably dependent on the console itself! For example I can use the Shift+Ins combination as described on a Cisco console, but than... the same does not work at all on a MikroTik console! Like I said... quite frustrating. Otherwise I like PuTTY, it's so lightweight and convenient... but this is really a blocking point. I have to find a way to copy text from the PuTTY....

---

### Post by TheFu on 2014-01-17
> **lz1dsb said:**
> I have to find a way to copy text from the PuTTY....

Select/paste text works extremely well with Linux-based terminals.  Any desktop-Linux will do it.

---

### Post by lz1dsb on 2014-01-18
> **TheFu said:**
> Select/paste text works extremely well with Linux-based terminals.  Any desktop-Linux will do it.

That was my expectation too :) It's kind of a standard feature for every terminal emulation application. Anyway - I'll make some screen shots these days and I'll post them here, to give you an idea of the issue. Maybe I'm doing something wrong, I don't know.

---

### Post by efflandt on 2014-01-18
The old original X way to copy text was L.mouse to highlight, middle-mouse (or both L and R mouse buttons) to paste. In that case it does not even use the clipboard. However, middle mouse is often pressing down mouse wheel which might slip you to a different line in some apps or trying to press left/right mouse simultaneously does not seem to work for me (brings up right click menu).

So the MS Windows way for Linux would be to highlight text, right click to copy, then either Ctrl+V (in gui like gedit), or in a text terminal Shift+Ctrl+V or Edit > Paste (since Ctrl+V often has other meanings in terminal or non-gui text apps).

While I use PuTTY in Windows to connect to *nix systems, I have never used it within Linux because every system I am aware of includes an ssh client program by default.

---

### Post by TheFu on 2014-01-18
> **lz1dsb said:**
> That was my expectation too :) It's kind of a standard feature for every terminal emulation application. Anyway - I'll make some screen shots these days and I'll post them here, to give you an idea of the issue. Maybe I'm doing something wrong, I don't know.

If you are on a Linux desktop OS and still using Putty, then you ARE DOING IT WRONG.

---

### Post by lz1dsb on 2014-01-18
> **TheFu said:**
> If you are on a Linux desktop OS and still using Putty, then you ARE DOING IT WRONG.
Yes, I'm on a Linux desktop... What do you mean by that? Is there a better open source terminal application? 
I know I can start an ssh session directly from the terminal, but with PuTTY I could have sessions which are preconfigured... That's the idea behind using PuTTY.

---

### Post by steeldriver on 2014-01-18
... fyi you can preconfigure terminal-based SSH sessions in a similar way using a ~/.ssh/config file

---

### Post by TheFu on 2014-01-18
> **lz1dsb said:**
> Yes, I'm on a Linux desktop... What do you mean by that? Is there a better open source terminal application? 
I know I can start an ssh session directly from the terminal, but with PuTTY I could have sessions which are preconfigured... That's the idea behind using PuTTY.

Yes, You are doing it all wrong, at least it appears that way from here. Or perhaps I do not understand the reason putty is being used from Linux at all?

Linux is NOT Windows. [This article]("http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed") tries to explain that a different thought process is needed to make the most of Linux/UNIX. A simple script or alias can replace all sorts of huge programs.  Don't fight the Linux-way, learn it, use it, make the computer your bitch. ;)

There must be at least 20 terminal apps in Linux - any of them are better with select/paste.
Every terminal program supports customization. Fonts, sizes, foreground, background, whatever. I've been using pure xterms for almost 20 yrs, but understand that people newer to Linux use other terminals.


Learn about the ~/.ssh/config file to store sessions.  
Learn about ssh-copy-id to make [remote ssh connections completely trivial]("http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication"). It is actually easier to be secure with ssh by using key-based credentials than fumbling around with passwords.

---

