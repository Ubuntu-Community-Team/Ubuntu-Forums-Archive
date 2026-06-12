---
title: "Email notifier"
date: 2013-06-06
forum: General Help
---

### Post by fizikz on 2013-06-06
I'm looking for an email notifier that has the following:

-works with multiple email accounts (gmail, hotmail, etc)
-has visual notification of unread emails in the notification area in gnome classic

Not absolutely necessary, but desirable niceties include:

-audible notification of new incoming emails
-showing the number of unread emails

---

### Post by ohnonot on 2013-06-07
try gnubiff.
i always thought it's ancient, but it's surprisingly up-to-date. needs some fiddling and twiddling.

---

### Post by Zill on 2013-06-07
How about "[mail-notification]("http://www.nongnu.org/mailnotify/")"?  It's in the repos.
```
sudo apt-get install mail-notification
```

---

### Post by fizikz on 2013-06-07
Thanks. mail-notification works but is a little buggy with the tooltips and it crashed on me a few times. gnubiff seems pretty great, but I can't add it to the gnome panel. Shouldn't the gnubiff package from the repositories have the ability to be added to the gnome panel?

---

### Post by Zill on 2013-06-07
> **fizikz said:**
> Thanks. mail-notification works but is a little buggy with the tooltips and it crashed on me a few times...
I am surprised at that - I have used it for years without any problems - and am still using it.

---

### Post by ohnonot on 2013-06-07
yeah, i also used both, m-n first. there was something which made me decide against mail-notification in the end, but it was not bugginess.
gnubiff is not added to the panel but goes in the systray, which usually resides in the panel. however it does not do that by default. i couldn't imagine why, but there it is. you have to execute it whith a switch like 'gnubiff -s' iirc.
open a terminal and type 'man gnubiff' - certainly has the answer.

---

### Post by fizikz on 2013-06-08
The crashes might be notification-daemon's fault and not that of mail-notification, but the end result is still the same. Glitches include things like the icon for mail-notification sometimes being only partially visible until I click on it, tooltips that appear half way down my screen instead of just below the system tray area, and the icon vanishing comopletely except for a white sliver if I click "mark mail as read." May it's just a question of massaging some of the settings. At least the mail checking part works well.

"gnubiff --systemtray" works for launching it in the system tray. Thanks for that. I modified it a bit by using the new mail and no new mail icons from cgmail, set the new mail text to bold, etc. It's great how configurable it is. The only issue I can see is that the background behind the icon is white, which clashes with the dark Ubuntu theme. Any idea on how to have the background match the rest of the system tray?

---

### Post by Zill on 2013-06-08
> **fizikz said:**
> The crashes might be notification-daemon's fault and not that of mail-notification, but the end result is still the same. Glitches include things like the icon for mail-notification sometimes being only partially visible until I click on it, tooltips that appear half way down my screen instead of just below the system tray area, and the icon vanishing comopletely except for a white sliver if I click "mark mail as read." May it's just a question of massaging some of the settings...
This sounds to me more like a video problem.  Maybe there is a better video driver for your graphics card.

---

### Post by ohnonot on 2013-06-08
> **fizikz said:**
> The crashes might be notification-daemon's fault and not that of mail-notification, but the end result is still the same. Glitches include things like the icon for mail-notification sometimes being only partially visible until I click on it, tooltips that appear half way down my screen instead of just below the system tray area, and the icon vanishing comopletely except for a white sliver if I click "mark mail as read." May it's just a question of massaging some of the settings. At least the mail checking part works well.now i remember it, yes, that was what it did on my system, too (a very plain, non-compositing install. don't see how graphics driver would come into it).> "gnubiff --systemtray" works... The only issue I can see is that the background behind the icon is white, which clashes with the dark Ubuntu theme. Any idea on how to have the background match the rest of the system tray?i really don't know how these things work in unity, but have you tried logging out and back in, with gnubiff autostarting?

---

### Post by fizikz on 2013-06-08
I'm using the proprietary nvidia drivers, and I don't see any other graphics related glitches. 

I'm running gnome classic (no effects) and not unity. I logged into unity and gnubiff didn't even show up in the system tray there. With regular gnome (not classic) the icon does show but looks worse than in gnome classic. The white background doesn't look nice but at least it does not affect functionality. Here is what it looks like:

[IMG]http://www.freeimagehosting.net/newuploads/j2lvk.png[/IMG]

One functional improvement would be if the unread email count would get updated if the emails get read, without having to constantly use 'mark mailboxes read' from gnubiff.

---

### Post by ohnonot on 2013-06-09
sorry, my bad, i guess this is the notification area, not the systray.
iirc, it is possible to change the background to your liking, but in a way that it does not change when changing themes.
i don't have gnubiff installed at the moment, so it's from memory.
i said: gnubiff is good, but it requires some fiddling.
i think it even says in the preferences that some preferences have to be changed via editing a text file. i recommend that. also all documentation you can find on gnubiff, like 'man gnubiff' in a terminal, or go to /usr/doc/gnubiff and see what's there...

---

### Post by fizikz on 2013-06-09
gnubiff is pretty configurable and the configuration file options can be edited from the gui preferences dialog box by ticking the "expert" preferences box. I did not find anything related to the background there, but I did find a few reports of others reporting the same issue: 

[http://sourceforge.net/p/gnubiff/bugs/53/]("http://sourceforge.net/p/gnubiff/bugs/53/")
[https://bugs.launchpad.net/ubuntu/+source/gnubiff/+bug/647399]("https://bugs.launchpad.net/ubuntu/+source/gnubiff/+bug/647399")

It is a minor issue but one that would perhaps be an easy fix. Another solution might be to make an icon image that fills that area and has the 'background' parts filled with the same color as the panel. Obviously that would not work if changing themes and would be rather inelegant. 

The more important change would be to have the mail count update if/when emails are read.

---

### Post by ohnonot on 2013-06-10
my solution was to use a selfmade icon with a neutral grey background; most my favorite themes are grayish anyway.
also it should be the same size as your panel icon preferences (i'm testing on lxpanel right now).
however this can change when you change the gtk theme; this is because gtk themes sometimes put a margin around things, sometimes not.
maybe the light grey background could be changed by tweaking ~/.gtkrc-2.0.
i don't know to what extent your DE and panel uses gtk2 or gtk3; with gtk3 things are slightly different.

here on my system i setup gnubiff with a gmail box with imap, updating once a minute (which is probably overkill) - and it updates correctly. what are your settings?

ps: i like the pop up to practically never time out, so i *must* look at my mail; the timeout can be set to much more than 90s if you edit ~/.gnubiffrc directly!

pps: 
[http://polishlinux.org/gnome/gnubiff-mail-notifications-on-your-desktop/](http://polishlinux.org/gnome/gnubiff-mail-notifications-on-your-desktop/)
[http://lovingthepenguin.blogspot.fi/2009/09/starting-up-gnubiff.html](http://lovingthepenguin.blogspot.fi/2009/09/starting-up-gnubiff.html)

---

### Post by fizikz on 2013-06-10
I may also make a custom icon image, or just live with it. 

I also set up one mailbox with imap and gmail, updating in 2 minute intervals, and it works great. I have another mailbox with pop3 and hotmail, updating every 2.5 minutes, and it sometimes gives errors saying the maximum logins for a 15 minute period have been reached. Also, sometimes I get notifications for one or more (20+) emails that were delivered days ago, even though they have long since been read. I'm not sure if that's an issue with gnubiff or not. 

I really like how non-intrusive and informative the gnubiff popups are. The 5 second timer works great for me.

---

### Post by cincinnatus13 on 2013-06-10
Could someone advise me on how this can be installed to the Gnome 3 panel itself? I did the configure, make, make install but it only shows up as a free floating icon on the desktop. I was under the assumption that it could run as a panel "extension" for lack of a better term.
What Gnome3 really could use is an easy to install extension that can be configured to fetch all mailboxes (ie. Gmail Notify but with many inboxes.)

---

### Post by fizikz on 2013-06-10
As suggested earlier, did you try:

```
gnubiff --systemtray
```

---

### Post by fizikz on 2013-07-10
I have a problem where sometimes, especially after some mail has been received and marked as read, gnubiff then reports "new" mail again, except that it is not new, but old mail. All the old mail has already been read. It seems to drudge up some random emails from previous days and displays a notification. Has anyone else noticed this? How can this be fixed?

---

### Post by fizikz on 2013-07-11
I should note that this problem of 'ghost' new emails which are actually old happens only with Hotmail, not with Gmail. I am using gnubiff for both accounts.

---

