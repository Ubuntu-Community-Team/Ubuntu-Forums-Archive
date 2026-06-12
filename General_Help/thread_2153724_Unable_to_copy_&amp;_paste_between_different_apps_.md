---
title: "Unable to copy &amp; paste between different apps 13.04"
date: 2013-06-12
forum: General Help
---

### Post by lelcamel on 2013-06-12
Hi,

I have this problem which prevents me from being able to copy text from putty to firefox, or from gnome-terminal to chrome.
I can copy & paste within an app but not outside of it.
I've looked for it on google and found a few threads regarding this issue in ubuntuforums.org, one of them said to install Parcellite and it should fix my problem.
I did install it, but it didn't fix my problem.
Any help would be appreciated as i'm very close to install windows on this laptop, the copy & paste is so much needed in my work and sadly it slows my work.
Thanks!

lelcamel

---

### Post by dragonfly41 on 2013-06-12
> .. i'm very close to install windows on this laptop, the copy & paste is so much needed in my work and sadly it slows my work

Any ubuntu fix is preferable to reverting to windows just for copy/paste feature!

If this is not an apps permissions problem .. you can try copy and paste into a text editor
then copy and paste for text editor to other app.

But this adds an extra step into your workflow which is annoying.

Some other discussion here .. but for older releases of ubuntu ..

[http://askubuntu.com/questions/3541/can-not-paste-into-terminal](http://askubuntu.com/questions/3541/can-not-paste-into-terminal)

---

### Post by ajgreeny on 2013-06-12
Copy/paste in which way; using Ctrl+C & Ctrl+V, using a right click and context menu, or just highlighting and then middle clicking to paste the buffer contents?

Without more detail it is impossible to understand what is not working.

---

### Post by Impavidus on 2013-06-12
Note that terminals use shift-ctrl-c and shift-ctrl-v instead of the ctrl-c and ctrl-v used by other programs. Select>right click>context menu and select > middle button work the same everywhere.

---

### Post by lelcamel on 2013-06-12
Dragonfly41: The last thing i want to do is to revert back to windows, i'm in love with linux :)
Okay, let me give you some more details;
Just after opening this thread i've continued looking for a solution and found Glipper which doesn't fully solve my problem but lessens it.
I am now able to copy & paste between different apps, but for example, while on putty (putty for Linux) i'm still unable to copy & paste, it does work but only within the putty window itself.
The key sequences i've tried are:
ctrl + c
ctrl + insert
ctrl + shift + c

Thanks!
lelcamel

---

### Post by dragonfly41 on 2013-06-12
In my PuTTY Configuration GUI I can use ..

Ctrl+C .. copy text
Ctrl+V .. paste text

---

### Post by gordintoronto on 2013-06-12
Try Highlighting text, right-click and select Copy.

Position the cursor, right-click and select Paste.

---

### Post by SeijiSensei on 2013-06-12
> **lelcamel said:**
> (putty for Linux)

Why would you use putty on Linux when there are superior terminal programs that ship with Ubuntu already?  Putty is nice when I'm on a Windows machine and need to connect over SSH, but it would never be my preferred terminal client on Linux.  I'd guess that putty for Linux probably doesn't do as good a job of implementing standard methods as do native programs like Terminal or Konsole which makes putty ill-suited for things like copy/paste.

---

### Post by monkeybrain2012 on 2013-06-12
Yeah, why would you use putty on Linux??

---

