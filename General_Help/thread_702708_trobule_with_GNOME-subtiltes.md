---
title: "trobule with GNOME-subtiltes"
date: 2008-02-20
forum: General Help
---

### Post by TheLions on 2008-02-20
After messing with some packages some of them were deleted. So when i try to one subtitle in GNOME Subtitles i get this (in terminal):

```
(gnome-subtitles:2139): Gtk-WARNING **: Ignoring the separator setting

(gnome-subtitles:2139): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
File open error:
[COLOR="Red"]System.NullReferenceException:[/COLOR] A null value was found where an object instance was required.
  at GnomeSubtitles.Player.get_FrameRate () [0x00000] 
  at GnomeSubtitles.VideoPosition.UpdatePositionValueLabel (TimeSpan newPosition) [0x00000] 
  at GnomeSubtitles.VideoPosition.ToggleTimingMode (TimingMode newMode) [0x00000] 
  at GnomeSubtitles.Video.UpdateFromTimingMode (TimingMode newMode) [0x00000] 
  at GnomeSubtitles.GUI.UpdateFromTimingMode (TimingMode mode) [0x00000] 
  at GnomeSubtitles.Global.set_TimingMode (TimingMode value) [0x00000] 
  at GnomeSubtitles.Global.CreateDocument (System.String path, System.Text.Encoding encoding) [0x00000] 
  at GnomeSubtitles.GUI.Open (System.String path, Int32 codePage, System.String videoFilename) [0x00000] 

```

please help me, this is only subtitle editor which have options which i need!

---

