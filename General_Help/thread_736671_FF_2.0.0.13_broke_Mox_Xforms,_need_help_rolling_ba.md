---
title: "FF 2.0.0.13 broke Mox Xforms, need help rolling back"
date: 2008-03-26
forum: General Help
---

### Post by ClarkePeters on 2008-03-26
Firefox 2.0.0.13 has broken my mozilla Xforms and I found out from the Xforms developers that I shouldn't use 2.0.0.13. 

How do I get back to 2.0.0.12?

I looked for a backup but couldn't find one.

Since I develop Xforms, I'm really paralysed so any help would be appreciated.

---

### Post by Bubba64 on 2008-03-26
Here is a download of FF you might be able to run sudo apt-get install firefox-2.0.0.12 and get it to go back I am not sure. I would wait for comments from more knowledgeable forum members.
[http://www.mozilla.com/en-US/firefox/2.0.0.12/releasenotes/](http://www.mozilla.com/en-US/firefox/2.0.0.12/releasenotes/)

---

### Post by Orky on 2008-03-26
I have an issue that is probably related, it just happened today after I installed 2.0.0.13. The download manager doesn't display downloaded files anymore, just the Clean Up button, and the Edit->Preferences dialog box doesn't work anymore at all, instead I get a window with a beige background, which looks like this:

```
[SIZE="4"]XML Parsing Error: syntax error
Location: chrome://browser/content/preferences/preferences.xul
Line Number 1, Column 1:[/SIZE]

[COLOR="Red"]urn false;'>Google Privacy Policy</a>
^[/COLOR]
```

I can't find a preferences.xul file using *locate*, so I am guessing it is stored inside an archive file.

Update: Restarting Firefox fixed the problem. I guess I updated Firefox while it was running and forgot to restart it...

---

### Post by Bubba64 on 2008-03-26
The link to FF 2.0.0.12 redirects you to 2.0.013 and the sudo command doesn't work I assume because it over wrote 2.0.0.12. When I look in synaptic there is an earlier version that can be forced but since I am hesitant to go beyond confirming that my advice is Bunk, and I am not having problems; hopefully somebody who actually knows what to due to fix the problems listed will chime in.

---

### Post by ClarkePeters on 2008-03-27
thanks for the input. I tried downloading Ff 2.0.0.12 and install it but I really don't know what I'm doing. 
Please help. Thanks

---

### Post by Bubba64 on 2008-03-27
I am not sure I am the best of help but what have you done since your post were you able to find the file you needed. I looked via google for a mirror with ff 2.0.0.12 but was not sure about what I found.

---

### Post by OoooMatron on 2008-03-27
The latest firefox update today broke a lot of webpages I visit with XML errors.

Don't they test these damn things properly? If I install updates from stable I expect them to be just that.

---

### Post by ClarkePeters on 2008-03-27
The only thing I was able to try was to download the 2.0.0.13 tar from Mozilla. I thought I might get lucky and that it was an Ubuntu thing and not a FF thing, but the trouble is with FF so that didn't help. I need to find the 2.0.0.12 tar or something (with some instructions on how to install it, i hope).

---

### Post by ClarkePeters on 2008-03-27
Hi lads and gents,
According to Mozilla, an upgraded Xforms 0.8.5 for FF 2.0.0.13 will be available within a short time frame ( a few days or a week maybe). 
see:
[http://groups.google.com/group/mozilla.dev.tech.xforms/browse_thread/thread/0f21aaf9884d5aef/d758a65f55f2337d#d758a65f55f2337d](http://groups.google.com/group/mozilla.dev.tech.xforms/browse_thread/thread/0f21aaf9884d5aef/d758a65f55f2337d#d758a65f55f2337d)


So, for me, I'll just hang out with FF 2.0.0.13 for awhile and work on other aspects of my project until then. :-\"

Thanks to those who took a look here and tried to help.
O:)

---

### Post by john-l on 2008-04-03
It looks like [version 0.8.5 of the Mozilla XForms Extension (MoXE) has been released]("https://addons.mozilla.org/en-US/firefox/addon/824"), although it has not yet been announced.  I have upgraded Firefox to 2.0.0.13 on one desktop running Kubuntu 7.10, and another running Ubuntu 7.10, and installed MoXE 0.8.5 on both.  Strangely, XForms forms load and work properly under Kubuntu, but not Ubuntu.  Under Ubuntu, pages with embedded XForms load as if MoXE were not installed.  I've messed around a bit with the packages installed on both systems, trying to make the Firefox-related set of packages the same on both systems, but the behaviour remains broken under Ubuntu.

Is anyone else seeing this behaviour?  Does anyone have any ideas?

---

### Post by john-l on 2008-04-09
> **john-l said:**
> Is anyone else seeing this behaviour?  Does anyone have any ideas?Ok, I figured out a solution.  I needed to first install the libstdc++5 package, then do a complete reinstall of the firefox package, and then the Mozilla XForms Extension (version 0.8.5) started working again (under Firefox 2.0.0.13).

---

