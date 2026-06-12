---
title: "terminal window size: i want pixel units"
date: 2019-12-22
forum: General Help
---

### Post by Skaperen on 2019-12-22
when i open a terminal window and get its window info, the size is shown in character units, such as 80x25,  i'd like to get the actual pixel units of the window.  i've seen cases where the character size is the same but the pixel size is somewhat different.

---

### Post by SeijiSensei on 2019-12-23
I suspect that's not possible. Terminal applications view the screen as a text-mode interface, so you get rows and columns.  I use KDE Konsole which is very configurable, and there's no way to see the terminal screen as pixels.

---

### Post by Skaperen on 2019-12-23
at some level X has to see this in pixels.  maybe the app, as well, since there are optional borders around the window.  i was hoping something can access this info.

what is especially strange (perhaps as a byproduct of most, but not all, size requests in character units getting a different size than requested) is that 2 different size requests can result in the same character size yet a different pixel size (the larger request has a few more rows of blank pixels under the last row of characters).  is X causing this, or is xfce4-terminal causing this?

i can do some screen captures if someone wants to see the results.  my script that starts the terminal puts its settings for the terminal program and my shell scripts can see what these are.

---

### Post by Holger_Gehrke on 2019-12-24
'xwininfo' outputs width and height in pixels, so that information definitely is available.

```

xwininfo -name "Terminal - XXXX@YYYYYYYY: ~"

xwininfo: Window id: 0x4600003 "Terminal - XXXX@YYYYYYYY: ~"

  Absolute upper-left X:  0
  Absolute upper-left Y:  57
  Relative upper-left X:  0
  Relative upper-left Y:  24
[B]  Width: 1920
  Height: 1023[/B]
  Depth: 32
  Visual: 0x4cd
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x4600002 (not installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+57  -0+57  -0-0  +0-0
  -geometry 190x47+0-0

```


Holger

---

### Post by Skaperen on 2019-12-25
ah, they "fixed" it.  it used to give it in characters for a terminal, so i quit using it.

---

### Post by Holger_Gehrke on 2019-12-26
It still gives characters for a terminal in the '-geometry'-line at the very end of the output.

Holger

---

