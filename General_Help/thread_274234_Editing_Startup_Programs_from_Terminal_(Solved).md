---
title: "Editing Startup Programs from Terminal (Solved)"
date: 2006-10-09
forum: General Help
---

### Post by PRGUY85 on 2006-10-09
Hey there:

I had all of this working with the Nvidia official beta drivers. Yet, I noticed that my wireless card requires the linux restricted modules which break the Nvidia beta drivers and messes up the X server...So I uninstalled the Nvidia beta drivers in order to install the other nvidia drivers as stipulated in method 1...but I need to remove the beryl-manager from my startup session since it doesn't work properly now and sends me back to the login window after showing the desktop for soem seconds...Since I can't enter the desktop for long using either of the available session options, is there a way to remove the beryl-manager from startup sequence from the terminal?

I can edit files using gedit from failsafe terminal since my X server is working. As I said, all I need is to get the startup file that has the programs I have there opening on startup to delete the beryl-manager so I can install the drivers...
Edit/Delete Message

---

### Post by angkor on 2006-10-09
Can't think of a clean way atm, but can't you just remove or rename the /usr/bin/beryl-manager file (to beryl-manager-backup or something)?

```
sudo mv /usr/bin/beryl-manager /usr/bin/beryl-manager-bak
```

That way the program won't launch when you start your session.

You could then access gnome and delete beryl-manager from the session startup programs.

---

### Post by jocko on 2006-10-09
I found that the startup programs set in gnome-session-properties are stored as .desktop files in ~/.config/autostart. It should work to just delete the one you want to get rid of:
```
rm ~/.config/autostart/beryl-manager.desktop
```
I haven't tested it myself, though...

---

### Post by hellmet on 2006-10-12
this thread helped me!!
thanks

---

### Post by SupRspi on 2007-01-09
Awesome!

jocko - you totally fixed my problem.  I'd tried to install beryl on my computer at work to see if it would run with lame onboard video, albeit slowly.

It would run, but wouldn't render anything other than a white screen.

However, I couldn't get into gnome-session-properties via terminal because I couldn't load a gnome session.  I just rm'd the file you mentioned and it worked like magic, even removing it from the gnome-session-properties applet automagically!

Just thought I'd post here to add some keywords in case someone else is looking for the same problem.

Cheers!

---

### Post by TriNitro on 2007-03-30
I've got the same problem, can't get into gnome, so I'm trying to find solutions from my XP partition. Here's hoping.

---

