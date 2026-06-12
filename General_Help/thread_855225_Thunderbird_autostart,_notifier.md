---
title: "Thunderbird autostart, notifier"
date: 2008-07-10
forum: General Help
---

### Post by sweetmoves on 2008-07-10
I recently downloaded Thunderbird and it works great although I would like it to start hidden in the background when I startup the computer and notify me when I get new email (some notification on the upper panel on the desktop for instance). There is a notifer in Thunderbird for Windows and - I am sure - there also is one for Ubuntu Linux.

---

### Post by SkonesMickLoud on 2008-07-10
You could add Thunderbird to your Startup Programs list.

Simply go to System >> Preferences >> Sessions >> Startup Programs tab.  Click on "Add".  For name, put whatever you'd like to call it, say "Thunderbird" and "thunderbird" (no quotes, lowercase) in the "Command" box.

However, I don't know how to make it hidden, or forked to a particular desktop.

And Thunderbird does include a notifier.  It pops up from the bottom right of my screen showing the sender, subject, and the first line or so.  It also rings a system bell if you have it enabled, which it is by default.

---

### Post by sweetmoves on 2008-07-10
SkonesMickLoud

I've alreday added it to the Startup Program list which is a good start I suppose :) Now only make it startup in the background. 

Someone else got any clue?

> And Thunderbird does include a notifier.
Yes, I get notified too, but only when I have Thunderbird open. If I go to Archive>Close (Ctrl + W) I thought it would run in the background, instead it seems to shut down like when I click Archive>Quit (Ctrl + Q). Open it up again and I get notified and system bell rings.

---

### Post by SkonesMickLoud on 2008-07-10
> **sweetmoves said:**
> SkonesMickLoud

I've alreday added it to the Startup Program list which is a good start I suppose :) Now only make it startup in the background. 

Someone else got any clue?


Yes, I get notified too, but only when I have Thunderbird open. If I go to Archive>Close (Ctrl + W) I thought it would run in the background, instead it seems to shut down like when I click Archive>Quit (Ctrl + Q). Open it up again and I get notified and system bell rings.

You could always run it on a different desktop.  Personally I really only use my 2nd desktop for Thunderbird.

Again though, I'm also trying to figure out how to start it on desktop #2 automatically.

---

### Post by PorkyPie on 2009-10-18
(This post was probably too late, but anyhow! :))

Hi. I'm not sure you can make it go to a specific desktop, but i have a solution that might work.


[LIST=1]
[*]Download Mozilla New Mail Icon from [http://moztraybiff.mozdev.org/releases.html](http://moztraybiff.mozdev.org/releases.html)
[*]Install it in Thunderbird.
[*]Go to System -> Preferences -> Startup Applications and click the "Add" button.
[*]ame it Thunderbird, and put the command as "thunderbird" (without quotation marks". You can leave the Comment field the way it is.
[*]Restart your computer, and thunderbird should be started in the backround. If you want to open thunderbird, click the icon in the system tray.
[/LIST]
That should work. I'm not sure whether you will have to conigure the Mozilla New Mail plugin, it should work straight away.

---

