---
title: "Terminal won't launch/load in desktop"
date: 2019-09-29
forum: General Help
---

### Post by dreadgreaves on 2019-09-29
Hello,

Alt + Ctrl + T and clicking will not load the terminal. Alt + Ctrl + f3 opens a terminal-like screen that asks me to log in instead. This isn't work flow friendly so  I noticed this problem after I downloaded google chrome to stream since Firefox had some issue... I since tried fixes removing google chrome virtual environment set up, redoing the locale-gen set up via Xterm and GUI.I have no idea if the locale-gen was fixed, however en_US and English were not altered in the GUI settings. I don't know what the problem is or what to do. I just got really tired of Windows 10 being slow and every update breaking it for me. Is there a recommended course for learning Linux/Ubuntu so I could understand this more myself?

I also tried safe boot UEFI by restarting and holding shift + up, from there I tried to restore packages/files, but that didn't work either. I appreciate any advice.

---

### Post by Skaperen on 2019-09-29
if you can run a file browser, look in your home directory for a file named "[COLOR=#0000cd][FONT=courier new]**.xsession-errors**[/FONT][/COLOR]".  it might have error messages describing the failure the terminal emulator had that prevented it from starting up (what you call "loading").

---

### Post by dreadgreaves on 2019-09-30
I was not able to locate that file by any means. Any suggestions on books for Linux?

---

### Post by TheFu on 2019-09-30
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - follow this in-order. Basic skills are needed before the next skill can be learned. Each skill builds on the prior skill learned and mastered.  After the first 250 pgs or so, then you can much more safely use google to search for answers.

"Ubuntu Desktop Guide"
"Ubuntu Server Guide"

To find files, I use a few different tools.   If you are really new, never forget that all Unix-like systems are case sensitive.  Searching for "FILE" isn't the same as searching for "file" or "File" or "filE". Each of those are different.  I'd use **locate** first, if I thought the file was over a day old. Every day, a fresh index of all the files on the system is made. This makes looking by filename nearly instance. 

If it is a new file, I'd use **find**, but find is a non-trivial command to use for someone really new to Unix.  Probably the easiest way to learn basic **find** commands is by searching for examples online.  For an administrator, mastering **find** is a necessary skill and crazy powerful.  Nothing like it exists on Windows. Nothing.

Then there are tools that know to search inside files for stuff and metadata, after they are indexed. Think of it as google for your systems - **recoll** - is one.  The indexes can become huge and take a long time to create. Recoll has a GUI. The other commands do not.  Recoll also has a non-GUI interface. I use this to find ebooks, music, and video files very fast across TBs of storage.

Most Linux books are out of date before they finally get onto paper.
My condensed blog post on how to learn Linux: [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)  The full post has many more resources.

I've been using xterms since the early 1990s. I've never liked the fancier, bloated terminals, pushed as defaults. xterm still works.  *-u8 -sb  -fa Monospace* are handy options for xterms.

<cntl><alt>-F1  thru F9 show different ttys.  c-a-F7 is the normal graphical TTY in Ubuntu (at least it is from 2008-2016). The others are "consoles" and are useful like a serial console connection. Unix is a different world than Windows, as you know.

locale-gen?  So, there is the system default, but all Unixen are multi-user, so the locale can be controlled by each user.  In Unix, environment variables are used 1,000x more than in Windows.  They are very powerful for configuring almost anything.  To make your timezone different, just change the TZ environment variable.  These variables are normally set in the ~/.bashrc file, if bash is the shell for the account. There are man possible shell programs, bash is just the default.
To get any GUI program to pay attention to environment changes, there are a few different ways, but logout and login is the easiest for someone new.  

There is almost no reason where a reboot of the system is needed to change any settings.

---

### Post by Impavidus on 2019-10-01
Risking to state the obvious, but .xsession-errors, like all files with a name starting with a dot, is a hidden file. You have to enable showing hidden files. I think in most file managers that's ctrl+h.

---

### Post by dreadgreaves on 2019-10-03
"Risking to state the obvious", well to most this is obvious, but I was oblivious. Thanks for the tip Impavidus.


Thank you for the suggestions TheFu. I felt like google searching for solutions was way worse than say stack overflow for code. I'm gonna try to work through the link you provided.

---

