---
title: "Opening ooWriter gets error messages"
date: 2007-07-27
forum: General Help
---

### Post by larryalk on 2007-07-27
When I try to open ooWriter from a konsole in Kubuntu Feisty Fawn I get the following error messages - how to fix?

ba@kinda ~ $ oowriter

(process:6047): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:6047): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:6047): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:6047): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

lba@kinda ~ $
(process:6047): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:6047): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

The ooWriter screen then comes up. 


Can anyone help on avoiding these error messages?

Larry

---

### Post by PointSource on 2007-07-27
It works though, doesn't it?

See how the same text seems to repeat itself? I think what happens is that the application tries to connect with the X server and fails for the first few attempts, then makes contact as the application main window appears.

If you type in the name of some other GUI program, like kate, the same kind of error messages will appear. No code is perfect.

---

### Post by larryalk on 2007-07-28
Hello PointSource.

You might be correct about trying to connect to X several times before it 'takes'.

I tried running kate and got no error messages.

Any other suggestions about X programs that generate similar error messages?

Larry

---

### Post by PointSource on 2007-07-28
Maybe try a GNOME based program?

---

