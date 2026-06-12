---
title: "firefox randomly closing"
date: 2005-06-06
forum: General Help
---

### Post by minimidgy on 2005-06-06
Whenever I am browsing through firefox, sometimes it just randomly closes after awhile.  It doesn't follow a pattern or a set schedule, it just seems completely random.  I've notice it does this sometimes on gstreamer also, but I think that might be a whole separate issue.

I'm not sure if this is a problem with the ubuntu version of firefox, or just the browser itself.  Any help would be appreciated.

---

### Post by blueplazma on 2005-06-06
[QUOTE=minimidgy]Whenever I am browsing through firefox, sometimes it just randomly closes after awhile.  It doesn't follow a pattern or a set schedule, it just seems completely random.  I've notice it does this sometimes on gstreamer also, but I think that might be a whole separate issue.

I'm not sure if this is a problem with the ubuntu version of firefox, or just the browser itself.  Any help would be appreciated.[/QUOTE]
 Can you give an error message?  Try running it from a terminal and looking at the error output.

---

### Post by minimidgy on 2005-06-06
[QUOTE=blueplazma]Can you give an error message?  Try running it from a terminal and looking at the error output.[/QUOTE]
See, that's the problem, there is no error message. It just kills itself

---

### Post by xerosis on 2005-06-06
it's happened to me a few times. mostly when loading media i think. do you have the mplayer-firefox plugin installed?

---

### Post by minimidgy on 2005-06-07
[QUOTE=xerosis]it's happened to me a few times. mostly when loading media i think. do you have the mplayer-firefox plugin installed?[/QUOTE]
i have it installed, but it doesn't close when I'm loading media.  It seems that it just closes it for no reason

---

### Post by Gtaylor on 2005-06-07
There are a few threads around about this. What graphics card are you running and did you install some kind of media plugin for Firefox like the mplayer one?

---

### Post by minimidgy on 2005-06-07
[QUOTE=Gtaylor]There are a few threads around about this. What graphics card are you running and did you install some kind of media plugin for Firefox like the mplayer one?[/QUOTE]

I'm using GeForce4 420 Go 32M

I installed the mplayer plug-in using ubuntuguide.org

---

### Post by Gtaylor on 2005-06-07
Some people have had to disable RenderAccel in their xorg.conf file, this is apparently a Nvidia driver issue. Mplayer has crashed my Firefox a bit but I don't think that's the issue here for you. I wish I had time to dig the URL up for you right now but I don't. Do some searching on Firefox crash and I'll come back and make sure you have it figured out later.

---

### Post by Halfling Rogue on 2007-07-28
I've got the same problem with Firefox 1.5 on Dapper. No error message, nothing, and my mplayer plugin doesn't seem to work, either (I still can't play DivX stuff like on tv-links.co.uk ).

---

### Post by itxaka on 2007-10-26
same here, SiS graphics card, mplayer-plugin and all codecs installed, firefox random closes. No explanation yet of why.

Could it be the touchpad? i think sometimes it closes when i touch it.

---

### Post by jfank on 2007-11-08
My Firefox closes whenever I go to bookmark a page.  It will just close out.  I uninstalled it and reinstalled it, and that didn't help at all.  I don't know what to do to get it to work correctly.  I tried to find a error message, but there was nothing.

---

### Post by bionnaki on 2007-11-08
run firefox from the terminal...and then copy/paste the error log when it crashes.

---

### Post by jfank on 2007-11-08
how do I run it from the terminal?  I'm still new to Linux, so ;yeah there is a lot that I dont know how to do.  Let me know how to run it from the terminal, and I'll copy and paste the error message.  I'm running on Kubuntu.

---

### Post by FuturePilot on 2007-11-08
I think for KDE it's Kmenu>Utilities>Konsole
and just enter in
```
firefox
``` and hit Enter. When it crashes it should leave an error message in the terminal.

---

### Post by jfank on 2007-11-08
here is what it told me.  And this is after I went to save a website int he bookmarks.


jfank2006@Justin-laptop:~$ firefox

(gecko:13235): Gtk-CRITICAL **: gtk_widget_get_parent_window: assertion `GTK_IS_WIDGET (widget)' failed

(gecko:13235): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window != NULL' failed

(gecko:13235): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault (core dumped)



I have no idea what this means or how to fix it. lol  Now if there is already a website saved in bookmarks I can go and view that site with no problem, but when I go to save a website in the bookmarks that is when it will just close itself.

---

### Post by libertas on 2007-12-23
ive got the same problem too

---

### Post by fragos on 2007-12-24
Firefox ocassionally dies for me when I try to browse the General Help forum of this site.  It stops responding.  After restarting Firefox it allways seems to work.

---

