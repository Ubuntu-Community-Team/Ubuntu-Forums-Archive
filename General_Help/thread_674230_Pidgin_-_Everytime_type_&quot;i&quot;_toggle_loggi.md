---
title: "Pidgin - Everytime type &quot;i&quot; toggle logging - HELP!"
date: 2008-01-21
forum: General Help
---

### Post by novus721 on 2008-01-21
This just started two days ago, and I have no idea why - every time I type "i" in pidgin, it turns on and off logging of the conversations - it is the toggle key when I go Options > Enable Logging with "i" as it's toggle key - I have looked all over the prefs and I cannot find toggle options to turn if off, any ideas??:confused:

---

### Post by jken146 on 2008-01-21
Tools -> Preferences -> Logging

---

### Post by Sidewinder1 on 2008-01-21
I had almost the exact thing except whenever I typed '?' it would toggle logging off and on. Pain in the neck every time I wanted to ask a question to type in (question mark). Huh (queation mark) I forget exactly which config file stores the information but the logging command that used to be commented out is not. I'll do some checking and respond later unless someone can tell you sooner. All you need to do is recomment the line that lists "I" toggling the logging.

---

### Post by novus721 on 2008-01-21
where?

I only see options to:

Log Format
Log all instant messages
log all chats
Log all status changes to system log

I have no other options - any ideas? 

** Thank you Sidewinder1, if you could get that, that'd be awesome

---

### Post by Sidewinder1 on 2008-01-21
The pidgin web site is down; doesn't surprise me. The only thing I can think for you to try, go to your home folder (you'll have to tell it to display hidden folders and files) and look for the .purple (that's right 'dot'purple) folder; open the accels text file with your text editor. See if you can find a line that looks like this:
(gtk_accel_path "<main>/Options/Enable Logging" i"")  if you find it make sure that it is commented out with a preceding  ";" semi-colon, no quotes. If it isn't, you've found your problem, simply put a semi-colon at the beginning of the line. I seem to remember finding another file, when I was having the "?" problem but I'll damned if I can find it now. It's one of the only things that I find difficult with ubuntu...GUI searching leaves much to be desired for us Window$ converts.

---

### Post by jerrykenny on 2008-01-21
maybe even look at system-preferences-keyboard shortcuts . . . . 

My Pidgn's a bit dotty as well, . . . . he came back without all his smileys the other day, dunno where hes left them :(

---

### Post by novus721 on 2008-01-22
> See if you can find a line that looks like this:
(gtk_accel_path "<main>/Options/Enable Logging" i")

That was it! I went through and found this:
```
; (gtk_accel_path "<main>/Options/Enable Logging" "i")
```

and so I just removed the "i", making it:
```
; (gtk_accel_path "<main>/Options/Enable Logging" "")
```

and now it works flawlessly - thanks for the help! :)

---

