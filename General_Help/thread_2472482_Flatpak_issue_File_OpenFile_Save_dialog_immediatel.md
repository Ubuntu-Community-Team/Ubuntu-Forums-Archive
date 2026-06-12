---
title: "Flatpak issue: File Open/File Save dialog immediately looses focus"
date: 2022-02-28
forum: General Help
---

### Post by vanadium on 2022-02-28
I use Flatpak because I like it more than Snap, but since some time, I see an issue with some flatpak installed applications (Chromium, Firefox, Thunderbird, Foliate). The issue is that a GTK File dialog ("Open File", Save dialog) immediately looses keyboard focus after it has launched. It acquires the colors of a non-focussed window, and receives no keyboard input.

Steps to reproduce the problem (here I use Chromium, but you can use Firefox, Thunderbird or Foliate if these are installed as a flatpak):

1) Open Chromium installed as a flatpak
2) Hit Ctrl+O: this opens the "Open File" dialog. First time after login, it goes well.
3) Close the dialog and hit Ctrl+O again. Now the dialog appears, but immediately its appearance changes to that of an unfocussed window. Typing a file name will cause the typing to appear in the window on the background, the location bar of Chromium.

This happens on Ubuntu 21.10 with its default flatpak version, Flatpak 1.10.2. Anyone else can reproduce this, or is this just me? I did not find anything on the internet about such issue.

---

### Post by vanadium on 2022-03-01
For those who care: I found it does not happen in xfce desktop, so it is a Gnome thing. It could be just Ubuntu 21.10 with current Flatpak 1.10.2, or wider. That is why I would like if a few people having *and* Gnome Desktop *and* flatpak could test using either Chromium, Firefox flatpak or Foliate, the only flatpak applications I have installed that use GTK3 file dialogs.

---

### Post by vanadium on 2022-03-03
An update and summary:

The issue (only Ubuntu 21.10 thus far) occurs
- both on Gnome Shell and Mate desktops, not on XFCE
- For Gnome Shell both on Wayland and Xorg
- For all containerized apps, i.e. Snap, Flatpak and  appimages.

The problem is related to xdg-desktop-portal and/or xdg-desktop-portal-gtk, a library allowing containerized apps to communicate with the main system. Issue was already reported here: [https://github.com/flatpak/xdg-desktop-portal-gtk/issues/137](https://github.com/flatpak/xdg-desktop-portal-gtk/issues/137)

---

### Post by vanadium on 2022-04-02
The issue I describe also occurs with the default snap version of Firefox in 21.10. Anyone willing to confirm?

- Open Firefox (snap)
- Hit Ctrl+O to open the file dialog - all is good: the first time it remains focussed
- Hit Esc to close the dialot
- Hit Ctrl+O to open the file dialog again: now it immediately looses focus after opening. If you start typing a file name, the file name probably will end up in your location bar behind the file dialog.

---

