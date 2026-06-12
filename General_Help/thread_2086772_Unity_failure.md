---
title: "Unity failure"
date: 2012-11-21
forum: General Help
---

### Post by kman2949 on 2012-11-21
Hi. Just now, I restarted my laptop only to find that, after signing into ubuntu, Unity did not appear to be working properly. I could tell because my background had been changed to the default background and the side bar and top bars are not visible or working as far I can tell. The only thing I was doing prior to restarting was downloading some libraries and fiddling around with aircrack and kismet. Terminal is working fine and all my files appear to be fine also. Please let me know what you think went wrong and how I can fix this. Thanks.

I am running Ubuntu 12.10 Quantal Quatzal on a Dell Studio 1555 laptop.

---

### Post by gerowen on 2012-11-21
Did you install any proprietary video drivers by chance?

---

### Post by kman2949 on 2012-11-21
I was just thinking of that and no I did not.

---

### Post by kman2949 on 2012-11-22
Sorry, when I said Unity failure I meant only a partial failure. The windows managers were still working but top bar, side bar, and background were not. I tried reinstalling headers and then removing nvidia drivers and installing nvdia-current but that caused the window manager to stop working and now Unity is in full failure.

EDIT:
After all of the previously described events, I ran these commands and the window manager is back to working again but still no progress with anything else.

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic

EDIT:

Thought it might help to include the new error messages I'm getting when starting firefox in the terminal here they are:

> (firefox:3118: Gtk-WARNING **: GModule (/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)

(firefox:3118: Gtk-WARNING **: Loading IM context type 'ibus' failed

(firefox:3118: Gtk-WARNING **: GModule (/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)

(firefox:3118: Gtk-WARNING **: Loading IM context type 'ibus' failed

(firefox:3118: Gtk-WARNING **: GModule (/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)

(firefox:3118: Gtk-WARNING **: Loading IM context type 'ibus' failed

(firefox:3118: Gtk-WARNING **: GModule (/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)

(firefox:3118: Gtk-WARNING **: Loading IM context type 'ibus' failed

(firefox:3118: Gtk-WARNING **: GModule (/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)

(firefox:3118: Gtk-WARNING **: Loading IM context type 'ibus' failed

---

