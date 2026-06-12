---
title: "firefox 17 package locked yet I still get prompted to upgrade?"
date: 2014-08-11
forum: General Help
---

### Post by Habitual on 2014-08-11
Xubuntu 14.04.1 LTS

I hate Firefox 31, so I removed it and installed [firefox-mozilla-build_27.0.1-0ubuntu1_amd64.deb]("http://hivelocity.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/f/firefox-mozilla-build/firefox-mozilla-build_27.0.1-0ubuntu1_amd64.deb")
I installed synaptic and locked the package, yet every time I (re)start Firefox I get a OSD bubble saying there's an update.

That or the attached.
Software Updater doesn't show any firefox-related updates.
Have a missed some thing obvious, or is it just an annoyance?

Thanks

---

### Post by vasa1 on 2014-08-11
See if this post by **Dennis N** is relevant: [http://ubuntuforums.org/showthread.php?t=2235031&p=13077158#post13077158](http://ubuntuforums.org/showthread.php?t=2235031&p=13077158#post13077158)

---

### Post by Dennis N on 2014-08-11
In this case, it is because you are using the Mozilla build, which does it's own check for updates independent of Ubuntu's package managers.

To stop Firefox phoning home and checking for updates, go to **Firefox Menu > Preferences > Advanced > Update Tab** and uncheck the update options.

---

### Post by vasa1 on 2014-08-12
> **Dennis N said:**
> In this case, it is because you are using the Mozilla build, which does it's own check for updates independent of Ubuntu's package managers.

To stop Firefox phoning home and checking for updates, go to **Firefox Menu > Preferences > Advanced > Update Tab** and uncheck the update options.
[deleted]...

I use Firefox direct from Mozilla ([https://www.mozilla.org/en-US/firefox/channel/#firefox](https://www.mozilla.org/en-US/firefox/channel/#firefox)) and so I do get the direct, delta updates mentioned when Mozilla pushes them to users and there is the option you mention.

BTW, I don't mind the updates because I use the [Classic Theme Restorer extension]("http://forums.mozillazine.org/viewtopic.php?f=48&t=2827985") and a little CSS of my own to make Firefox look "pre-Australis". That's mainly because default Australis doesn't allow having tabs and the url bar on the same row.

---

### Post by Habitual on 2014-08-12
> **Dennis N said:**
> **Firefox Menu > Preferences > Advanced > Update Tab** and uncheck the update options.
Thanks!

We'll see if it stops.
I should have known it was a FF "thing" by the FF logo on that dialog box shown in the attachment.

---

