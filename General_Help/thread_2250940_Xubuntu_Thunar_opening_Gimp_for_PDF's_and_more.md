---
title: "Xubuntu Thunar opening Gimp for PDF's and more"
date: 2014-11-01
forum: General Help
---

### Post by Brandon_MacEachern on 2014-11-01
Please tell me I'm not the only one finding Xubuntu 14.10 being stupid with PDF's and opening them in GIMP and not something more suitable, like document viewer?

In fact, it's messing up with a lot of files!

Here you go with a video showing what I am seeing.  Please excuse Mr. Samuel Jackson in the background, he tends to swear.

[https://www.youtube.com/watch?v=NaDXdQd7x_Y](https://www.youtube.com/watch?v=NaDXdQd7x_Y)

---

### Post by Bucky Ball on 2014-11-01
*Thread moved to **General Help**.*

Right click the file you want to open>'Open With'>choose an app and tick the box at the bottom of the window that asks if you want the app to be the default for these types of files.

---

### Post by Brandon_MacEachern on 2014-11-01
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

Right click the file you want to open>'Open With'>choose an app and tick the box at the bottom of the window that asks if you want the app to be the default for these types of files.
Thank's for not watching the video and seeing this is NOT working.  :) While I appreciate the help, you'll find if you watch the video, this is not working at all, and no MIME type is being honored, except on the desktop itself.

---

### Post by Bucky Ball on 2014-11-01
Apologies, but must admit I don't watch every two minute video people post to get an answer for if they've used the obvious fix. Get through a lot of posts here. Best to just tell us what you've tried in your first post. ;)

So, we know the obvious solution is working once, when you manually choose 'Open With' and set Doc Viewer as the default app, but it's defaulting back to Gimp. Hmm. Further thinking needed. I run xfce4 BTW so I'll have a sniff about ... :-k

---

### Post by vasa1 on 2014-11-01
> **Brandon_MacEachern said:**
> Please tell me I'm not the only one finding Xubuntu 14.10 being stupid with PDF's and opening them in GIMP and not something more suitable, like document viewer?

In fact, it's messing up with a lot of files!
...
Is your system a pure Xubuntu or it is Ubuntu with some aspect of Xubuntu added to it?

---

### Post by Bucky Ball on 2014-11-01
It could be an idiosyncrasy of the new 14.10. It has been out a week and is wet behind the ears. There are a lot of posts about it. These things will (hopefully) get ironed out in time. 

Have you searched the forum and net to see if anyone else is having this issue?

* And there is. 

> If you recently upgraded to glib >= 2.41, then that's the reason Thunar
isn't respecting the default app you've set.

See the following bug report for details:

[https://bugzilla.xfce.org/show_bug.cgi?id=11212](https://bugzilla.xfce.org/show_bug.cgi?id=11212)

From [HERE.]("http://xfce.10915.n7.nabble.com/Thunar-does-not-recognices-mimetype-asociation-in-PDF-and-OpenDocument-td44404.html") 
And from the same thread, this:

> I recently had a problem with thunar starting from session or by
xfce-shortcuts. They had an incomplete set of environment variables
which results in some more or less funny file associations.

If the problem fixes by killing an restarting thunar ("killall Thunar",
then if no thunar running start thunar from shell with "Thunar". ), you
might have a similar problem like me.

Possible Workarounds:

(1) Disable xfce-session / autostart feature (not shure, which one),
instead first start thunar from a shell.

(2) Check environment of your thunar processes (with "strings
/proc/<pid-of-defect-thunar>/environ | grep ^XDG_DATA_DIRS") and compare
this to the environment in you shell. Check at least variables
$XDG_DATA_DIRS and $PATH.
Sometimes thunar seem to get launched by dbus session bus (config file
/usr/share/dbus-1/services/org.xfce.Thunar.service). Then the set of
environment variables is a bare minimal.

I try to work around this by patching PATH and XDG_DATA_DIRS evironment
variables for the dbus session bus. I've done this by patching
/etc/X11/xdm/Xsession.


This is OpenSUSE 13.1. There might be significant differences to other
distributions.
I'm not shure if this is an OpenSUSE of XFCE-Problem. 

One thing to try for a start is opening Thunar from a terminal (just type in 'thunar') and going through the motions. When you get to the part where it opens Gimp even though it's set for Doc Viewer, go to that same terminal and check the output. Post it back here. Might give us a clue what is going wrong.

---

### Post by ajgreeny on 2014-11-01
You are not alone!
See [http://ubuntuforums.org/showthread.php?t=2250511&p=13156129#post13156129](http://ubuntuforums.org/showthread.php?t=2250511&p=13156129#post13156129) where someone else has exactly that problem with pdf files.  There is no response yet to my final suggestion at post #4 of that thread so I have no idea if it got the OP any nearer to an answer.

---

### Post by buzzingrobot on 2014-11-01
I see it, too, in Xubuntu 14.10.  It wants to open CSS files in Abiword, PDF's in Gimp, etc.  The right-click option in Thunar to alter the default is not always offered.

---

### Post by Bucky Ball on 2014-11-01
Well, there we go. It can be replicated. You are NOT alone! 

Update everyday for awhile until it goes away, that is my prescription (unless you want to start tweaking code, which would be great!). There would possibly be a bug report on Launchpad about it. Perhaps have a check and post to it.

---

### Post by buzzingrobot on 2014-11-01
This -- [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1382977](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1382977) -- looks like the relevant bug.

---

### Post by Brandon_MacEachern on 2014-11-02
Yea, that bug report wasn't promising, being a fix will be available in Xubuntu 15.04.  I'd rather not use a BETA for a fix, I'd expect 14.10 to be fixed of this.

The only reason I jumped to 14.10 over 14.04, drivers for my laptops GPU finally support WebGL in Chrome properly without black screening the canvas, and some of my work software require Chrome AND Canvas support.

---

### Post by Elfy on 2014-11-02
At least for the pdf issue - edit the file

```
pkexec mousepad /usr/share/applications/mimeinfo.cache
```

Find the pdf line

> application/pdf=gimp.desktop;evince-previewer.desktop;evince.desktop;

and remove Gimp

> application/pdf=evince-previewer.desktop;evince.desktop;

save it

---

### Post by vasa1 on 2014-11-02
> **Elfy said:**
> At least for the pdf issue - edit the file

```
pkexec mousepad /usr/share/applications/
```

...
Filename is missing?

---

### Post by Elfy on 2014-11-02
> **vasa1 said:**
> Filename is missing?

thanks - added it :)

---

### Post by buzzingrobot on 2014-11-02
mimecache.info here now includes "> application/pdf=evince.desktop;gimp.desktop;evince-previewer.desktop; and PDF's launch in Evince.

---

