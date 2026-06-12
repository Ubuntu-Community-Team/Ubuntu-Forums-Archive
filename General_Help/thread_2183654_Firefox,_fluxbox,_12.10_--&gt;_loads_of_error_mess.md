---
title: "Firefox, fluxbox, 12.10 --&gt; loads of error messages. What's wrong?"
date: 2013-10-25
forum: General Help
---

### Post by ArlieS on 2013-10-25
I *had* a working installation of Ubuntu 12.10 desktop, with Unity.  I installed 2 months of updates, and Unity self-destructed. I then installed kubuntu-desktop and fluxbox, to try them out.... and because I had no clue how to fix Unity. 

Now I'm seeing the following from firefox:

(firefox:3367): Gtk-CRITICAL **: IA__gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(firefox:3367): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox:3367): Gtk-CRITICAL **: IA__gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox:3367): Gdk-CRITICAL **: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3367): Gdk-CRITICAL **: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed

(firefox:3367): Gtk-CRITICAL **: IA__gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(firefox:3367): Gtk-CRITICAL **: IA__gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(firefox:3367): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox:3367): Gtk-CRITICAL **: IA__gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

I don't know whether these would also have occurred in Unity - launching from the dash, I've no idea where the errors messages would have gone, but with my current half baked fluxbox installation, I'm launching firefox from an xterm window.

Has the Unity version of Firefox got window manager dependencies? I.e. does it require some piece of Unity and/or gnome to be functional?

For what it's worth, gnome-terminal isn't fully functional either.

---

