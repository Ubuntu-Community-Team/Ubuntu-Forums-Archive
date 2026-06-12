---
title: "nm-applet fails to appear in the lxpanel"
date: 2015-02-13
forum: General Help
---

### Post by Rex Bouwense on 2015-02-13
When Lubuntu 14.04 was released the nm-applet would not start by default.  Until a fix was released the work around was to launch it manually in default applications for lxsession.  That worked fine.  Recently, after numerous updates the nm-applet once again will not launch.  However, I am connected to my wireless provider.  There just is no indication in the lxpanel.  The previous work around does not appear to work this time.  I can start the applet with
```
sudo nm-applet
```
but it will not survive a reboot.  Any help would be appreciated.

I do get this error message in the terminal when using the above command.

** (nm-applet:3443): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-o28th37GkB: Connection refused
nm-applet-Message: using fallback from indicator to GtkStatusIcon

---

### Post by sudodus on 2015-02-13
If nothing else helps, I would add ***nm-applet*** in **autostart**.

Last time this was recommended, I learned to ***avoid sudo*** (which would make it necessary to use it 'always' afterwards, probably because some configuration file was hi-jacked by root). Maybe ***gksudo*** or ***sudo -H*** would be better, but it worked for me with regular user privileges.

---

### Post by Rex Bouwense on 2015-02-13
Thanks for the response.  I have added nm-applet to my autostart list but it will not autostart.  Everytime I reboot the network GUI is blank so I have to add nm-applet but it does no good. (gksudo also starts the nm-applet).  I am thinking that some recent update may be the problem, because after the initial problem it ran good until this morning.  I am connected to my wireless.  It is just that there is no indicator in the LXPanel unless I open it manually with sudo or gksudo.  Weird.

---

### Post by sudodus on 2015-02-13
So it happened this morning. Probably that update has not trickled down to me yet. I'll be back if/when I get hit by it ...

---

