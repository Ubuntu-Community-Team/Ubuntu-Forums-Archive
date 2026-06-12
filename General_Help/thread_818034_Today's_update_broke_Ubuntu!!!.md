---
title: "Today's update broke Ubuntu!!!"
date: 2008-06-04
forum: General Help
---

### Post by frogitts on 2008-06-04
So I updated my computer this morning, restarted, and now many of my programs don't work. 
1) Firefox 2 reports a segmentation fault (I'm working from the Firefox 3 beta 5), 
2)gnome-session-properties reports not being able to connect to session manager, (after stating "None of the authentication protocols specified are supported and host-based authentication failed."), 
3)the login window manager took about 5 minutes to start up for the first time, now it starts up fine,
4)Amarok can't find the "dcopserver" program and reports the xml in the transfer list is invalid (and now opens up in two windows, inexplicably), and
5)My external Hard Drive is now mounted in read-only mode, and stays in read only mode even after unchecking read-only mode and remounting in System > Administration > Storage Device Manager
6)Skype and Pidgin work, it seems, although they start about 3 minutes after Ubuntu starts, though I have them set to load on startup. 
6)Finally, when I press the red power button on the right hand side of the top panel, gnome-panel quits. I found out after doing this and resarting gnome-panel via terminal, that gnome-panel has practically same error as gnome-session-properties: 
```
(gnome-panel:9370): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
(gnome-panel:9370): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -4 and height 24
```
I would imagine that the second error is unrelated, but I left it in just in case.

I'm sure there are more errors out there, but those are the ones that I've found. Things like calculator, open office, f-spot, firefox 3, and a few games still work. Why did this happen?


And why do I have (did I have) 460MB of thumbnails in a /home/user/.thumbnails?!?!? That's insane! But probably unrelated.

---

### Post by kpkeerthi on 2008-06-04
> **frogitts said:**
> 
And why do I have (did I have) 460MB of thumbnails in a /home/user/.thumbnails?!?!? That's insane! But probably unrelated.

Nautilus caches the preview images in there. The more file you have and the more you browse with nautilus, the more space it tends to occupy. 

Unfortunately, it has to be manaully cleaned. You can choose to keep the most recently used thumbails and delete the rest using this command:
```
find ~/.thumbnails -iname "*.png" -atime 14 -exec rm '{}' ';'
```
This command will keep the thumbnails that are used in the last 14 days and deletes the rest. 

Optionally add this command to crontab and schedule it to run every 15 days.

---

### Post by frogitts on 2008-06-04
Nice solution, thanks! I think something like that should be an option within Nautilus, but I will probably use yours or something like it in the days and weeks to come.

In other news, my computer started working again. I don't know why, but the only thing I changed was this: I read something about opening a terminal using Ctrl+Alt+F1, so I tried it just to see what would happen - and of course, I was switched out of X, etc. So I just did "sudo shutdown 0" and cancelled the dialog that it gave me about recovery module, etc. and rebooted the system automatically without shutting down the entire computer (i.e. I never saw the GRUB menu). Now the panel starts up fine. I then opened up firefox 3 to look at the forums again, and it asked me to make it the default browser (since I had firefox-2 as the default). I just clicked "ok" before realizing what I did, then quit firefox 3 to see if firefox-2 was still broken. I am now typing this from firefox-2, no segmentation fault. My hard drive now functions perfectly (although it didn't load on system start), and the session manager now opens.

So somehow I fixed a segmentation fault and an inaccessible session-manager by restarting Ubuntu through the terminal. Let me tell you, that was the easiest fix for one of the scariest problems I've had with Ubuntu.

---

### Post by tiggsy on 2010-02-04
2 years down the line, I had the same problem with firefox refusing to load. on trying to do so via terminal i got:

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Segmentation fault

my shutdown button also reacted in the same way discussed, but although i tried ```
sudo shutdown now
```, which usually fixes that bug, it was not working, and neither did using a terminal obtained from control-alt-F1 and doing ```
sudo shutdown 0
```

But I looked for the folder in my home folder (.thumbnails) referred to above, and emptied out all the files in there, leaving the folders alone.

Firefox now loads, so I am assuming that it's all due to this poor backup computer's painful need of space.

---

