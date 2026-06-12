---
title: "Slingscold suddenly stopped working!"
date: 2018-05-14
forum: General Help
---

### Post by deanr2 on 2018-05-14
I'm running Ubuntu Mate 16.04 and often use[d] Slingscold alongside the Mate Main Menu to search for and open apps. I tried using it today and the icon just pops and doesn't open the programme. I tried uninstalling, purging and reinstalling it but it still refuses to open.

I typed 'Slingscold' into the terminal and got the following output (sorry, no idea how to paste terminal output proper into a thread):


(slingscold:2428): Gtk-CRITICAL **: IA__gtk_icon_info_load_icon: assertion 'icon_info != NULL' failed


** (slingscold:2428): CRITICAL **: slingshot_frontend_indicators_set_active_no_signal: assertion 'self != NULL' failed


** (slingscold:2428): CRITICAL **: slingshot_frontend_app_item_change_app: assertion 'new_icon != NULL' failed


(slingscold:2428): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion 'GDK_IS_PIXBUF (pixbuf)' failed


(slingscold:2428): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion 'GDK_IS_PIXBUF (pixbuf)' failed


(slingscold:2428): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion 'GDK_IS_PIXBUF (pixbuf)' failed


(slingscold:2428): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels_with_length: assertion 'GDK_IS_PIXBUF (pixbuf)' failed


(slingscold:2428): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion 'GDK_IS_PIXBUF (pixbuf)' failed


(slingscold:2428): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion 'GDK_IS_PIXBUF (pixbuf)' failed


(slingscold:2428): GLib-ERROR **: /build/glib2.0-prJhLS/glib2.0-2.48.2/./glib/gmem.c:328: overflow allocating 18446744073709551615*18446744073709551615 bytes
Trace/breakpoint trap (core dumped)



This means absolutely nothing to me and I'm not advanced enough to do anything too complicated in the command line or otherwise. And apart from switching from Cairo-dock to Plank and resetting the panel I can't think of anything else I've done recently that could be responsible for it not working. 

Any help would be greatly appreciated.

---

### Post by cruzer001 on 2018-05-14
NoobsLab has dropped it from their ppa.  Where are you finding a download source?

---

### Post by deanr2 on 2018-05-14
I tried downloading it today from App Grid and from the websites Sourceforge and yes, the noobslab.com site.

It's still working on my Mint 18.3. Can I expect it to stop working soon on that OS too, then?

---

### Post by cruzer001 on 2018-05-14
AppGrid not showing it either.  If you will provide a download link I will install it.

---

### Post by deanr2 on 2018-05-14
Thanks for the help, cruzer001.

There's one link here which downloads as a tar.gz file which I haven't managed to work out. I can open it but can't run or install it: [https://sourceforge.net/projects/slingscold/?source=typ_redirect](https://sourceforge.net/projects/slingscold/?source=typ_redirect)

Here's the command line code from noobslab which I've also tried: [https://www.noobslab.com/2015/03/slingscold-launcher-fixed-for-all.html](https://www.noobslab.com/2015/03/slingscold-launcher-fixed-for-all.html)

FYI, as of now my App Grid still seems to let me install and uninstall Slingscold but still won't launch it. I'm working so I haven't logged out or rebooted - maybe it will disappear then :-/

---

### Post by cruzer001 on 2018-05-14
I gave the sourceforge link a shot.  Had to use google translate on the read me files.

It seem to compile just fine, no missing dependences.

But in the end I had the same result as you.  It just wont launch either in terminal or /usr/bin and no errors reported.

Thats as far as my knowledge can take me on this one, sorry.

---

### Post by deanr2 on 2018-05-15
Hmm. Interesting. Well, thanks for trying anyway cruzer001!

---

### Post by rraginggoblin on 2018-09-21
It apparently is missing some icons: IA__gtk_icon_info_load_icon: assertion 'icon_info != NULL' failed
Running it with mint-x theme gave me this error as well but switching back to mint-y theme it launched fine

---

