---
title: "Using Ubuntu without mouse. How? Any advice?"
date: 2007-12-01
forum: General Help
---

### Post by Serguei_89 on 2007-12-01
Hi

**My goal is simple. Use mouse as little as possible when using Ubuntu.** Motivation? I got a laptop and mouse pad is just so uncoftably slow to use. 

Several specific areas:

Desktop environment: Which of the environments you think is best suited for this? Gnome, KDE, or XFCE? I'm willing to switch to any of those.(got KDE and GNOME now)

Window management: Say I want to position 2 windows in a certain way on the screen. How would I do that without a mouse? I think Compiz-fusion allows certain "window-rules" to be set and then snap windows into that. I couldn't set it up an I'd rather not use Compiz and similar graphic enhancements. But if there is any window manager or tool that would acomplish this, please mention.

Web-browsing: I got extension Hit-a-Hint(or something like that) to browse around without mouse. The extension "surfkeys" is incompatible with latest firefox versions. Any advice on achieving similar functionality?

File managment: What file manager should I use for greatest speed? I used Total Commander on Windows and even though I tried Krusader, Gnome Commander, I couldn't get the same functionality. But in any case, what File manager would you advise? 

Amarok: Are there any scripts to help with this? I'm going to look myself, but if anyone knows, please share. 

Managing processes: I understand I could use command-line for all my process managment. Should I just read the man page for top and kill and use that? Or are there any better tools?(Note: I already use Tilda and Yakuake for instant switch to the terminal)

Handling applications: I use Katapult and Deskbar applet to run applications and search for stuff. Everything seems ok here.

And if any of you know any other utilities and programs that would help me nearly abandon the mouse, please leave a reply.

Note: I know I'll need mouse for some things no matter what. But I'd still want to rely mostly on keyboard.

---

### Post by -grubby on 2007-12-01
I don't understand? Why not just get a little mini mouse at walmart?

---

### Post by Serguei_89 on 2007-12-01
when I used keyboard-only for file managment using Total Commander on Windows, it was way faster than draggin and dropping things with mouse. I think the same will extend for other tasks as well. (For example it's faster to use apt-get install and apt-cache search to look for and install software then point in click in synaptic or adept.)

---

### Post by spupy on 2007-12-01
There are window managers specially designed to be used without mouse. Two examples - **Ion** and **WMii**. But they are really "hardcore" WMs.

If you don't want to use ion or wmii, you can write scripts that use programs such as **wmctrl** to control the windows around, and then assign some keybindings to these scripts. But i haven't read the man page of wmctrl and am not sure how easy that would be.

For managing processes: htop is just what you need. It's terminal app, but is a good program with enougth options. (supports mouse if needed.)

Appart from these (or in addition), all other apps that come to my mind that require less mouse are all terminal, i.e. not graphical: vi/nano for text, mpd+mpc for music, mc for file management.

---

