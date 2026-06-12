---
title: "Flash Player issues in Firefox"
date: 2016-03-28
forum: General Help
---

### Post by gdesilva on 2016-03-28
Hi, I am running Firefox 45.0, adobe-flashplugin 1:20160310.1-0ubuntu0.14.04.1 under Ubuntu Studio 14.04. I have no issues playing flash videos but if I click the full screen button while the video is playing, it takes literally 3-4 seconds to get to full screen. During this period I get the audio playing but the screen is black. Same process happens when minimizing the screen. No problems with Chromium which responds instantaneously. 

Appreciate if anyone has any suggestions to fix this issue.

Thanks

---

### Post by ajgreeny on 2016-03-28
What hardware?

The version of flash you will have in FF is 11.2.202.577 unless you install the freshplayerplugin from the nilarimogard ppa repository, when you will get the same version as you have in chromium.
Use commands ```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
```
I have been using this for over a year with no difficulty on my 14.04 so I believe it is worth trying.
I can not promise it will speed up the flash in FF but it might help to have the latest version instead of 11..2.202.577.

---

### Post by gdesilva on 2016-03-28
@ajgreeny, Thanks for the suggestion. I did install freshplayerplugin as you suggested but there is no improvement at all. 

I am running US 14.04 64bit on a HP small form factor PC with Intel Core i7-2600 CPU @ 3.40GHz and 8GB of RAM and a ATI Radeon HD 5400/6300 graphics card . There is no lag or delay in playing the video and the problem occurs only when I try to maximize or minimize the screen and as mentioned it is not an issue with Chromium.

EDIT: Installed Midori and no problems so it appears it is specific to Firefox.

---

### Post by gdesilva on 2016-03-29
I have done a bit more checking....and noticed that if I run firefox from terminal and move the cursor on to any of the youtube buttons such as maximize, minimize etc, I get a heap of warning messages as follows and as long as I do not move the cursor no error messages are displayed. The same warning messages are continuously displayed when the maximize icon is pressed.


(firefox:2626): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.40.2/./gobject/gsignal.c:3408: signal name 'text-insert::system' is invalid for instance '0x7fd1cc034880' of type 'MaiAtkType27'

(firefox:2626): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.40.2/./gobject/gsignal.c:3408: signal name 'text-remove::system' is invalid for instance '0x7fd1cc034880' of type 'MaiAtkType27'

(firefox:2626): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.40.2/./gobject/gsignal.c:3408: signal name 'text-insert::system' is invalid for instance '0x7fd1cc034880' of type 'MaiAtkType27'

(firefox:2626): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.40.2/./gobject/gsignal.c:3408: signal name 'text-remove::system' is invalid for instance '0x7fd1cc034880' of type 'MaiAtkType27'

(firefox:2626): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.40.2/./gobject/gsignal.c:3408: signal name 'text-insert::system' is invalid for instance '0x7fd1cc034880' of type 'MaiAtkType27'


Anyone has any idea what these warning messages are and how to fix them?

Thanks

---

