---
title: "CalDAV help in Ubuntu 17.10"
date: 2017-10-31
forum: General Help
---

### Post by mike370 on 2017-10-31
Hi There,

I'm new to Ubuntu, coming from many years on Mac.  This may be a total noob question, but I'm having trouble figuring out how to connect Gnome Calendar to a CalDAV based Calendar service. 

I did some searching for instructions and the best I found was this blog post about it:

[https://www.ctrl.blog/entry/gnome-caldav](https://www.ctrl.blog/entry/gnome-caldav)

If I understand correctly it says that I need to: input my CalDAV info./credentials into Evolution, and the data will then flow through to Gnome Calendar.  I never have to use Evolution again, but I do need to keep it installed on the machine as the bridge between Gnome Calendar and the CalDAV service.

This struck me as odd because Gnome Calendar is included in Ubuntu 17.10 but Evolution is not.  Why would I need to download an application that is not part of a distribution in order to make an app that is part of the distribution do its job? 

I understand that if I use Google or MS Exchange for my calendar then I don't need to use Evolution but that confused me too.  Why would Ubuntu be making it easier for people to connect to proprietary cloud services but harder to connect with open standards?  Again I'm very new to GNU/Linux, I'm trying to make it work for philosophical reasons, but these implementations seem counter to everything I've read.  

What am I missing?

TL;DR -- How do I set up a CalDAV account in Gnome Calendar on Ubuntu 17.10?

---

### Post by aeyoun2 on 2017-11-17
GNOME Calendar, GNOME To-do, and even the calendar and notifications in the GNOME message tray are all powered by the Evolution Data Server (EDS). GNOME requires that you have *evolution-data-server* installed, but you don&#8217;t need to install the Evolution client (*evolution*).

If you install Evolution you get the most complete interface for managing the Evolution Data Server. GNOME Calendar and a couple of other specialized productivity client programs are fairly new compared with Evolution, so they don&#8217;t _yet_ have comprehensive configuration and management systems.

The reason you can configure Google and Exchange accounts is that GNOME/Ubuntu has included user interfaces for configuring these accounts in Evolution Data Server but have not included interfaces for configuring generic CalDAV accounts. Notably, when you setup a Google account you add your Google calendars over CalDAV. So &#8230; yeah. It&#8217;s all about priorities and configuration of CalDAV accounts haven&#8217;t been prioritized. See [https://www.ctrl.blog/entry/windows-pim-sync-partnersonly](https://www.ctrl.blog/entry/windows-pim-sync-partnersonly) (which does apply to Linux despite the Windows focus).

Anyhow, install Evolution, setup your account, uninstall Evolution if you don&#8217;t want to keep it. (Evolution is pretty great, by the by!)

---

