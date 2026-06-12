---
title: "Disable Evolution's Integration with Calendar"
date: 2007-02-20
forum: General Help
---

### Post by nyxynyx on 2007-02-20
Hello! How do i disable Evolution's integration with calendar?

---

### Post by dcstar on 2007-02-20
> **nyxynyx said:**
> Hello! How do i disable Evolution's integration with calendar?

I seem to remember it is one of the Plugins which you should be able to turn off in Evolution (not 100% sure on this, though).

---

### Post by pandu.rs on 2007-03-05
--disable-eplugin              Disable loading of any plugins.

Though i figured out how to turn off loading any plugins, i could not figure how to disable a specific plugin. Moreover i want to know what all plugins evolution loads.. so that i can decide if it is necessary for me.

My current issue that evolution hangs while loading CalDAV plugin :( 
(I am using evoltion-exchange account)

any ideas on how to solve this will be of great help to me. Thanks

---

### Post by pandu.rs on 2007-03-05
Got it

Edit->plugins

seems like this menu entry will not appear when --disable-eplugin option is used

---

### Post by cyberswat on 2007-03-06
I used Evolution to subscribe to a calendar feed from my website.  I have since wiped the machine and reinstalled Ubuntu.  I disabled the calendar on the site and began getting error messages on the website that my ip address was attempting to access the event feed.  This concerns me because I had not configured the new installation to point to the site.

In an attempt to stop my machine from accessing the event feed I started evolution and have disabled every plugin available ... I would like to know why this machine is still attempting to connect to my site on a regular basis with an unconfigured Evolution installation and I would love to make it stop as it has been filling my web servers logs with errors attempting to connect on an hourly basis.  I didn't tell the new installation to connect to this site and I am concerned of the security implications.

---

### Post by someonestolemyname on 2008-03-17
It sounds like you copied over your old home directory form your previous install. The Evolution settings are kept in ~/.evolution. This would be why the setting are carrying over.

Otherwise, I don't know. You must have done it manually again.

Daniel

---

