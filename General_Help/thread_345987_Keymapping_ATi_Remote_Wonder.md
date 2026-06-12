---
title: "Keymapping ATi Remote Wonder"
date: 2007-01-25
forum: General Help
---

### Post by CocoAUS on 2007-01-25
I've got a Remote Wonder (usb device, some controls work without any configuration) that I would like to map the rest of the buttons on.  Volume, arrows, clicking, and numbers work fine, but I would like to customize the controls.  How would I go about doing this?

---

### Post by bogolisk on 2007-02-16
Your question is not clear. For which application are you trying to do the keymapping?

I don't have the remote wonder but the remote wonder II. It sends HID events via the input layer. If your application understand XF86 keys then you can use xev + xmodmap (create a ~/.xmodmaprc file)  to define keys such as XF86AudioPlay. E.g. if xev reports a keycode 162 when you press the STOP button then you can put in your ~/.xmodmaprc:


[INDENT]...
keycode 162 = XF86AudioPause
...
[/INDENT]

If your application suports LIRC, then the easiest way is to use inputlirc. E.g.:

~/.lircrc:

[INDENT]...
begin
  button = KEY_PLAY
  prog = mplayer
  config = play
end
...
[/INDENT]

~/.freevo/lircrc
[INDENT]...
begin
        prog = freevo
        button = KEY_FORWARD
        config = FFWD
end
...[/INDENT]

---

