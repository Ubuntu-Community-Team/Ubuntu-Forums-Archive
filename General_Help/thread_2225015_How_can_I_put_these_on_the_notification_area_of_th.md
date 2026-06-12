---
title: "How can I put these on the notification area of the panel?"
date: 2014-05-19
forum: General Help
---

### Post by pretty_whistle on 2014-05-19
I have ubuntu 14.04 with xfce desktop.

I want the wireless icon and the power icon to be on the panel but they're not in the list you can choose from.  How can I put these there?

---

### Post by matt_symes on 2014-05-19
Hi

They should appear when you boot into your desktop.

I would start off by posting your xsession-errors.log file in your home directory to see if that holds any clues as to why they are not starting.

Kind regards

---

### Post by pretty_whistle on 2014-05-19
Where is that?  I cant find [COLOR=#000000] xsession-errors.log.[/COLOR]

---

### Post by matt_symes on 2014-05-19
Hi 

My mistake. It should be

.xsession-errors

Notice the leading dot or period. It`s a hidden file in your home directory.

To see it in the file browser hit <ctrl> and h at the same time. This will display hidden files.

I may not be able to look at it until wednesday though.

Kind regards

---

### Post by Frogs Hair on 2014-05-19
Have you installed the xfce4-goodies package ? The package includes the indicators you are looking for and more.

---

### Post by Luke M on 2014-05-19
Apologies if this question seems stupid, but do you have them installed? I think many of the plugins are not installed by default.

---

### Post by pretty_whistle on 2014-05-19
> **Frogs Hair said:**
> Have you installed the xfce4-goodies package ? The package includes the indicators you are looking for and more.
Really?

No I haven't installed it.  How do I install it?

Edit:  never mind.  I see it.

Thanx!

---

### Post by pretty_whistle on 2014-05-19
Thanx again frog! :)

Marking this as solved.

---

### Post by Frogs Hair on 2014-05-19
> **Luke M said:**
> Apologies if this question seems stupid, but do you have them installed? I think many of the plugins are not installed by default.

Ive not installed the XFCE desktop on 14.04 yet but have used it on 12.10-13.10 and the package is not installed by default . 

> This package will install the following Xfce4 related plugins:
  * Extra artwork (xfce4-artwork)
  * Battery levels monitor (xfce4-battery-plugin)
  * Clipboard history (xfce4-clipman-plugin)
  * CPU frequency management plugin (xfce4-cpufreq-plugin)
  * CPU utilisation graphs (xfce4-cpugraph-plugin)
  * Date and time plugin (xfce4-datetime-plugin)
  * Disk performance display (xfce4-diskperf-plugin)
  * Filesystem monitor (xfce4-fsguard-plugin)
  * Generic monitor, for displaying any command result (xfce4-genmon-plugin)
  * Mail watcher (xfce4-mailwatch-plugin)
  * Mount plugin (xfce4-mount-plugin)
  * Network load monitor (xfce4-netload-plugin)
  * Notes plugin (xfce4-notes-plugin)
  * Quick access to bookmarked folders, recent documents and removable
    media (xfce4-places-plugin)
  * Tiny launchers (xfce4-quicklaunchers)
  * Sensors plugin, frontend to lm-sensors (xfce4-sensors-plugin)
  * Smartbookmarks plugin (xfce4-smartbookmark-plugin)
  * System load monitor (xfce4-systemload-plugin)
  * Timer plugin (xfce4-timer-plugin)
  * Command line with history (xfce4-verve-plugin)
  * Wireless lan monitor (xfce4-wavelan-plugin)
  * Weather monitor (xfce4-weather-plugin)
  * Keyboard configuration (xfce4-xkb-plugin)
  * Archive management for Thunar (thunar-archive-plugin)
  * Media tags editor for Thunar (thunar-media-tags-plugin)

It'll install some standalone applications too:
  * Tiny text editor (mousepad)
  * Images viewer (ristretto)
  * Archive manager (squeeze)
  * CD/DVD burner (xfburn)
  * Frontend to dictionnaries (xfce4-dict)
  * Notification daemon (xfce4-notifyd)
  * Tool to take screenshots (xfce4-screenshooter)
  * Task manager (xfce4-taskmanager)
  * Terminal emulator (xfce4-terminal)

Some packages are only suggested because they bring too much dependencies,
but you may find them interesting:
  * Cellular modem plugin (xfce4-cellmodem-plugin)
  * Search plugin, frontend to locate (xfce4-linelight-plugin)
  * DBus messaging plugin (xfce4-messenger-plugin)
  * Another commandline plugin (xfce4-minicmd-plugin)
  * Frontends to MPD (xfce4-mpc-plugin, xfmpc)
  * Radio plugin (xfce4-radio-plugin))
  * GNOME applet plugin (xfce4-xfapplet-plugin)
  * Fast-user switching plugin (xfswitch-plugin)
  * ThinkPads HDAPS plugin (xfce4-hdaps)
  * Additional thumbnailer for Thunar (thunar-thumbnailers)
  * GIO/GVfs frontend to manage connections to remote filesystems (gigolo)
  * Media player (parole)
  * Power Manager (xfce4-power-manager)

This is a metapackage to ease upgrades, installations, and provide a
consistent upgrade path from previous versions. It can safely be removed with
no ill effects.



---

