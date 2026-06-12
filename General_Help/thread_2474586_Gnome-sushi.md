---
title: "Gnome-sushi"
date: 2022-05-03
forum: General Help
---

### Post by Onesimus on 2022-05-03
I have recently installed Ubuntu 22.04, and would like to get gnome-sushi to work.

I am currently able to get a preview of the file - that all works fine.
However, I should then be able to open the file whilst still in Sushi, but the button in the Top Right corner always says 'Open with WSLView'   rather than the designated application for that file type (e.g. 'Open with Writer').

Any ideas ?

---

### Post by him610 on 2022-05-03
```
apt show gnome-sushi
```
> ... Description: sushi is a quick previewer for nautilus
 Sushi is a Gtk+ and Javascript-based quick previewer
 for Nautilus, the GNOME desktop file manager.
 Sushi is a DBus-activated service. It is capable of previewing
 documents, PDFs, sound and video files (using GStreamer),
 some text files, and possibly others in the future.
 .
 To activate the preview, left-click the file and hit space.
 The preview can be closed by hitting space again, or escape.

Does not reference anything about opening or activating file.

---

### Post by Onesimus on 2022-05-03
Screenshots would say otherwise ....

[IMG]https://149366088.v2.pressablecdn.com/wp-content/uploads/2021/07/gnome-sushi-file-preview-photo-on-ubuntu-desktop.jpg[/IMG]

---

### Post by deadflowr on 2022-05-03
Sushi's open with dialog is set to use whatever the default appliactions is set in the Settings > Default Applications.
[s]As far as I can tell it does not care about whatever the file association for any file type is.[/s]


Edit: Scratch that.
I guess some file types can be set in the file's properties open with settings.
I see that file types for those types listed in Default Applications use the settings in Default Applcations
And other file types seem to use whatever it set for the file associations  themselves in the File's properties settings.

If that makes any sense.
(FTR, it doesn't make sense to me, but that is how I see it working)

---

### Post by Onesimus on 2022-05-04
Weirdly, when I google 'WSLView' it indicates that is a:
  *  Component of Windows 10 Linux Subsystem Utility*

I've never had Microsoft Windows on this machine ?!?
So something is awry.

---

