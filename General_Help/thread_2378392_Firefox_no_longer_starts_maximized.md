---
title: "Firefox no longer starts maximized"
date: 2017-11-22
forum: General Help
---

### Post by Keith_Helms on 2017-11-22
Since the last update, Firefox no longer starts maximized like it has done for years.  How do I fix this?

---

### Post by &amp;KyT$0P# on 2017-11-22
Does [this thread]("http://forums.mozillazine.org/viewtopic.php?f=38&t=3034375") help?

---

### Post by vasa1 on 2017-11-22
Can't you force it to open maximized via your window manager?

I changed from "force"to "apply initially". That gives me more flexibility.

---

### Post by Keith_Helms on 2017-11-25
> **vasa1 said:**
> Can't you force it to open maximized via your window manager?

I changed from "force"to "apply initially". That gives me more flexibility.

I'm using Xubuntu and I've never come across any configuration options in the window manager for specific applications.  Since my first post I have found that I can edit xulstore.json in the firefox profile directory and manually set width and height to 1920x1030 and sizemode to maximized.  That gets it opening maximized again for a while, although after doing that it has reverted to a 640x400 window once already, so the change is not permanent.

---

### Post by #&amp;thj^% on 2017-11-25
vasa1 is using kwin for that option shown.
But just to be clear, Firefox overwrites window manager rules by restoring window size / position after startup

Note that current Firefox releases haven't used localstore.rdf for quite some time and that only xulstore.json is used to store data about windows.
The window size is no longer stored (sizemode: normal) and thus is it impossible in current releases to force a maximized window or full screen mode on startup.
See also: [https://support.mozilla.org/en-US/questions/1149222](https://support.mozilla.org/en-US/questions/1149222)

---

### Post by Keith_Helms on 2017-11-25
> **1fallen said:**
> vasa1 is using kwin for that option shown.
But just to be clear, Firefox overwrites window manager rules by restoring window size / position after startup

Note that current Firefox releases haven't used localstore.rdf for quite some time and that only xulstore.json is used to store data about windows.
The window size is no longer stored (sizemode: normal) and thus is it impossible in current releases to force a maximized window or full screen mode on startup.
See also: [https://support.mozilla.org/en-US/questions/1149222](https://support.mozilla.org/en-US/questions/1149222)

Yes, I came across that thread when I was googling for a solution.  So far, my edits to xulstore.json have survive a few restarts without being overwritten.  If it's really true that firefox no longer saves size/position when you quit, hopefully mozilla will get enough complaints to restore that feature.

---

### Post by mc4man on 2017-11-25
> **1fallen said:**
> vasa1 is using kwin for that option shown.
But just to be clear, Firefox overwrites window manager rules by restoring window size / position after startup

Note that current Firefox releases haven't used localstore.rdf for quite some time and that only xulstore.json is used to store data about windows.
The window size is no longer stored (sizemode: normal) and thus is it impossible in current releases to force a maximized window or full screen mode on startup.
See also: [https://support.mozilla.org/en-US/questions/1149222](https://support.mozilla.org/en-US/questions/1149222)
With Ubuntu (compiz) & Gnome (mutter) FF always opens at previous window size so don't think that link is 100% accurate..

---

### Post by #&amp;thj^% on 2017-11-25
> **mc4man said:**
> With Ubuntu (compiz) & Gnome (mutter) FF always opens at previous window size so don't think that link is 100% accurate..

Agreed, And I myself have no problems with the window size>>using XFCE and Compiz, But I don't want it maximized at first opening either. :)FWIW.

---

### Post by vasa1 on 2017-11-25
> **Keith_Helms said:**
> I'm using Xubuntu and I've never come across any configuration options in the window manager for specific applications.  Since my first post I have found that I can edit xulstore.json in the firefox profile directory and manually set width and height to 1920x1030 and sizemode to maximized.  That gets it opening maximized again for a while, although after doing that it has reverted to a 640x400 window once already, so the change is not permanent.

I remember Toz, Xfce guru, posting details about using **devilspie** to control window settings. Openbox and KWin have elaborate rules for dealing with windows. I don't know about compiz and mutter.

I don't know if devilspie will work with wayland.
Couple more questions:

If you maximize Firefox and then quit it during a session and restart it in the same session, do you have the window opening non-maximized? Or does this happen only once per session.

And what happens with a new profile?

---

### Post by Keith_Helms on 2017-11-26
> **vasa1 said:**
> I remember Toz, Xfce guru, posting details about using **devilspie** to control window settings. Openbox and KWin have elaborate rules for dealing with windows. I don't know about compiz and mutter.

I don't know if devilspie will work with wayland.
Couple more questions:

If you maximize Firefox and then quit it during a session and restart it in the same session, do you have the window opening non-maximized? Or does this happen only once per session.

And what happens with a new profile?

Once it decides to no longer start maximized, no number of quits and restarts makes it do otherwise.  I also tried the reset option which blows away your profile and creates a new one.  That didn't work either.   The only thing that DID work for me was manually editing the xulstore.jsof file and changing the width, height and sizemode settings.

---

