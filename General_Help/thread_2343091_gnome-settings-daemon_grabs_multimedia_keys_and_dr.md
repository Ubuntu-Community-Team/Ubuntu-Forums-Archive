---
title: "gnome-settings-daemon grabs multimedia keys and drops mute since upgrade 16.0"
date: 2016-11-13
forum: General Help
---

### Post by David_Madison on 2016-11-13
I have a Thinkpad X1 (1st Gen) running Ubuntu (previously on 14.04)

It has multimedia buttons on the side for:  XF86Launch1, XF86AudioMute, XF86AudioRaiseVolume, XF86LowerVolume and XF86AudioMicMute.  They used to work fine in 14.04, even to the extent that the little orange light inside the 'mute' key would come on when muted and turn off when not.

I upgraded to 16.04 and none of them worked anymore.

I realized that they were getting grabbed by (but not used by) the Keyboard shortcuts as accessible from gnome-control-center or unity-control-center.

When I turned off the keyboard shortcuts for the media keys, I was then able to see the keycodes with xev, and hence was able to use something like xbindkeys for a hack of a solution.

All except for the input mute, which still isn't working.  So I check with acpi_listen and see that that the buttonpress is being registered, just as it is for the other media keys, but when I press it, I see:

 
```
(gnome-settings-daemon:14711): GLib-GIO-WARNING **: Dropping signal AcceleratorActivated of type (uuu) since the type from the expected interface is (ua{sv})
```

When I kill gnome-settings-daemon then I can properly see the input mute key in xev and grab it as needed.

How can I keep gnome-settings-daemon from trying to (and failing to) grab this key?

---

### Post by David_Madison on 2016-11-13
Posted to askubuntu:

    [http://askubuntu.com/questions/848856/gnome-settings-daemon-grabs-multimedia-keys-and-drops-mute-since-upgrade-16-04](http://askubuntu.com/questions/848856/gnome-settings-daemon-grabs-multimedia-keys-and-drops-mute-since-upgrade-16-04)

---

