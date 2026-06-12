---
title: "Getting PuTTY to work on desktop Linux"
date: 2014-04-28
forum: General Help
---

### Post by craig10 on 2014-04-28
Hi all,

I'll preface this question by stating that I'm a reformed Windows user who switched to Ubuntu for my desktop machine a little over a month ago. However, I've been using Linux on the command line over SSH for years.

Being a former Windows user I've been happily using PuTTY for those years. One of the things I like about PuTTY is that it will record session logs. However, I don't see that option in the default SSH client under Ubuntu (GNOME Terminal), which is why I was happy to see PuTTY in the Ubuntu Software Centre. You can save yourself reading the rest of this post if you can recommend an SSH client that will save and log sessions. I'm well aware that I can use "ssh remote.server.com" in GNOME Terminal but I want logging. I've also read all the negative and patronising reactions of astonishment to people who admit to using PuTTY under Linux, so that will tell you I've probably hit all the similar PuTTY-related posts on this site.

(I've tried piping SSH output to "tee" [ssh [EMAIL="user@remote.server.com"]user@remote.server.com[/EMAIL] | tee logfile] but the output is full of non-printable characters. Same with using "script". And I've seen a reference to using ~/.ssh/config for saving sessions which I will look into if I can't get PuTTY to work.)

I installed PuTTY, and I can log in and the session is logged. So what are my problems? I had three, but I'm down to one and a half:

1) I cannot copy text to the clipboard from within PuTTY, and
2) I cannot run multiple sessions.

At the moment I have over thirty browser tabs open on these subjects (and have closed many more), so I've tried to do my research. But if I can't get these two issues solved, then PuTTY will be of no use to me under Ubuntu.


**Item 1 -- Copy to the clipboard**

On Windows just highlighting text in PuTTY copied it to the clipboard, and a single right-click pasted. I finally figured out pasting on Ubuntu by using Shift+Insert instead of right-clicking. I've read various articles about copying, and none of the following suggestions have worked for me:

1) Simply highlighting the desired text does not automatically copy it to the clipboard.
2) There is no right-click menu, and the right-click does not copy the highlighted text to the clipboard.
3) Middle mouse click or simultaneously clicking the left and right mouse / touch pad buttons does not work.
4) Shift+Ctrl+C does not work. Ctrl+C obviously doesn't work either.
5) Ctrl+Insert doesn't work.
6) Shift+Delete does not work.
7) Shift+Insert and Shift+Ctrl+Insert will copy the highlighted text and simultaneously output it on the command line. However, the text is not actually copied to the clipboard, as shown by hitting Shift+Insert or Ctrl+V in another program -- e.g., gedit. This behaviour is of no use to me.

It occurs to me that I can work around the copying issue by opening the session log and doing it from there. Not ideal, but better than nothing.


**Item 2 -- Multiple sessions**

If I already have one PuTTY session open, clicking the PuTTY icon in the launcher just brings up that session, and there is no menu in the PuTTY window title bar where I might find an option to open a new session. Right-clicking the launcher icon does not bring up an option to start a new simultaneous session either.


If you can help with either of these or, as I said, suggest a different terminal program that stores sessions and logs sessions, I'd appreciate it. I'm running the stock Unity desktop on 13.10. If there's any other information I can provide please let me know.

Thanks.


Craig

---

### Post by dragonfly41 on 2014-04-28
I've no direct experience of multiple putty sessions (one session is enough for my purposes and I'm an infrequent user of PuTTY) but being curious I found this

[http://ubuntuforums.org/showthread.php?t=2181307](http://ubuntuforums.org/showthread.php?t=2181307)

which recommends use of "screen".

[COLOR=maroon][Later edit][/COLOR]

And I confess that I don't understand the copying problem

My sessions are stored in ~/.putty/sessions as text files .. easily edited.

And if in the GUI I can use on any field in focus .. right click .. select all .. then Ctrl+C (copy) .. Ctrl+V (save) to a text file.

I must be missing some point here.

[COLOR=maroon][Later edit]

And finally ... have you tried FileZilla (offers multiple tabs/sessions).
[/COLOR]

---

### Post by HermanAB on 2014-04-28
Howdy,

You need session logging and then you list a whole bunch of things that do not work and which would drive me up the wall.

You should run ssh inside screen.  It does everything you want and much more:
[http://www.gnu.org/software/screen/manual/screen.html](http://www.gnu.org/software/screen/manual/screen.html)

---

### Post by craig10 on 2014-06-05
Hi Dragonfly and Herman,

Thanks for your replies. My apologies for not coming back here for so long, but the to-do list doesn't get any shorter, and to be honest I've been rather down about this particular issue (and not being able to figure out using PuTTY [or Terminal] with key-based authentication), which has required me to keep my old XP machine sitting on the desk next to me in order to use SSH to my satisfaction.

While I appreciate your answers, I think one of my issues has been misunderstood.

First, copying text in PuTTY simply isn't working. It just ain't. No keyboard or mouse button combination I have tried has succeeded in copying text from the terminal to the clipboard.

Second, I think my requirement to run multiple sessions of PuTTY (or any other terminal that meets my needs) has been misunderstood. I want to run multiple sessions of the SSH client, not multiple log-ins on the server. Screen and Tmux do the latter, if I understand correctly, and while I've been aware of Screen for a few years, I have never found a real need to use it.

I need to run multiple session of PuTTY (or, as I say, any other terminal client that provides logging) that are each connected to different servers. Again though, even though PuTTY will allow me to create and save sessions for multiple servers (which, as Dragonfly points out, are saved in ~/.putty/sessions as plain-text files), I can only run one active PuTTY window at a time. There is simply no option to open a second (or third or fourth, etc.) PuTTY window while another session is active. If I right-click on the PuTTY icon in the launcher, I get only two options: "PuTTY SSH Client" and "Unlock from Launcher". The first option -- the default -- simply brings up the existing session window. There is no option to bring up the PuTTY configuration dialogue from where I might be able to open another session.

As for FileZilla -- I'm confused by that suggestion. It's an FTP client, not a terminal client. In case I was missing something I looked for a terminal option, but didn't find it.

One poster in the thread to which you pointed me, Dragonfly, suggests GNOME Connection Manager as an alternative to PuTTY. I'll look into that, but these issues with PuTTY simply baffle me, as I seem to be the only one experiencing them!


Craig

---

### Post by steeldriver on 2014-06-06
I just loaded up putty on my 12.04 box to take a look. FWIW I use putty everyday from Windows.

You can start multiple instances and background them from the command-line

```
putty & putty &
```

Any time you need another, go to a terminal again and 

```
putty &
```

The copy/paste seems to use the XWindows primary buffer by default, instead of the clipboard i.e. I was able to copy just by highlighting and paste using **middle click** (on a 2-button mouse that's usually mapped to concurrent left and right clicks). I will take a longer look and see if there's a way to configure it to use the clipboard buffer.

---

### Post by dragonfly41 on 2014-06-06
Have you tried **[COLOR=#0000cd]secpanel[/COLOR]** from Ubuntu Software Centre?

---

### Post by SeijiSensei on 2014-06-06
I like the KDE terminal client, [Konsole]("http://kde.org/applications/system/konsole/").  It has multiple tabs, nice color schemes, and an infinite scrollback history if you choose. I used PuTTY on a Windows machine the other day, and it was nowhere near as pleasant an experience as using Konsole.

---

### Post by CharlesA on 2014-06-06
> **SeijiSensei said:**
> I like the KDE terminal client, [Konsole]("http://kde.org/applications/system/konsole/").  It has multiple tabs, nice color schemes, and an infinite scrollback history if you choose. I used PuTTY on a Windows machine the other day, and it was nowhere near as pleasant an experience as using Konsole.

I run Gnome, so Konsole pulls in a bunch of KDE stuff, but I still use it.

Otherwise, it's just straight terminal.

I only use Putty on Windows.

---

### Post by Toz on 2014-06-06
Item #1:
For me. highlighting the text to be copied in putty and middle-clicking in another app successfully copies the text.

Item #2:
Middle-clicking on the putty icon in the dash starts up another putty instance.

If these don't work for you, does your mouse/touchpad middle-click work otherwise in the system?

---

### Post by craig10 on 2014-06-06
**Steeldriver** and **Toz**,

You are both stars. Thank-you. I am now able to copy data from the PuTTY terminal and paste it into another application, and with either technique run multiple sessions of PuTTY. Don't know why I didn't think of trying to launch PuTTY from the command line.

Thank-you again.


**Dragonfly** and **SeijiSensei**,

Thank-you for your suggestions. I will look into both.


Next on the to-do list: Figuring out key-based authentication with PuTTY and [mounting an encrypted drive read-only]("http://ubuntuforums.org/showthread.php?t=2228150"). :)


Craig

---

