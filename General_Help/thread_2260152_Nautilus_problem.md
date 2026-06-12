---
title: "Nautilus problem"
date: 2015-01-09
forum: General Help
---

### Post by Philip_Liao on 2015-01-09
I am new to Ubuntu. I have following problem which I have no capability to understand let along to solve it. Error message below:
"(nautilus:3871): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files"

I Google searched Gtk and found one section recommending to re-install Gtk through Synaptic as I have install synaptic. Unfortunately that is not possible because Gtk had been installed. Then found another one using command line and it return with a message that said I have the latest Gtk installed. It's either nothing to do with Gtk or broken installation which I have not have a clue what it is. Should I just erase the disk and fresh install again? Any guidance how to solve this is highly appreciated.

I try to run Heimdall & Heimdall-frontend in hope that I can bring unbrick the soft-bricked old TMO Samsung Galaxy Vibrant S back to stock ROM Froyo. Try Odin on Windows 8.1 did not work. Try Heimdall in Windows 8.1, I encountered USB drivers issue. Heimdall USB drivers broke Samsung connection and no device shown on Heimdall-Frontend GUI panel in Windows 8.1. Android after all is a fork of Linux and therefore, logically Linux is a better platform to do what I am trying to do here. 

Another strange behavior is that Heimdall & Heimdall-frontend were properly installed through gdebi installer. Yet, when I type in Heimdall-frontend in the terminal, I got following return message:
"heimdall-frontend: error while loading shared libraries: libQtXml.so.4: cannot open shared object file: No such file or directory"

When I was using Ubuntu 8, 9 10, I have no such problem and actually love Ubuntu. But since 14.04 onward, there seems to be a lot problems in Ubuntu.

---

### Post by mc4man on 2015-01-09
> **Philip_Liao said:**
> I am new to Ubuntu. I have following problem which I have no capability to understand let along to solve it. Error message below:
"(nautilus:3871): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files"

It's just a *warning* usually seen when opening nautilus as root, in that case can be  ignored.

(- if you're opening a root file browser with sudo nautilus I'd suggest you stop, use either 
gksudo nautilus
or
sudo -H nautilus

---

