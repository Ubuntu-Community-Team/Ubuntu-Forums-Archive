---
title: "Unable to compile gtk+"
date: 2007-02-23
forum: General Help
---

### Post by Kingfield on 2007-02-23
I get this error during make (no errors during compile)

```
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_title'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_is_private'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_description'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_free'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_type_register_static_simple'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_create'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_surface_set_fallback_resolution'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_load_from_file'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_visited'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_modified'./.libs/libgtk-x11-2.0.so: undefined reference to `g_key_file_set_double'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_mime_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_is_private'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_has_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_key_file_get_double'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_applications'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_ps_surface_set_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_uris'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_new'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_description'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_title'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_surface_get_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_to_file'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_group'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_create_for_stream'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_application'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_remove_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_mime_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_move_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_set_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_groups'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_app_info'./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_added'
collect2: ld returned 1 exit status
make[4]: *** [gtk-query-immodules-2.0] Error 1
make[4]: Leaving directory `/home/kingfield/Desktop/gtk+-2.10.0/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/kingfield/Desktop/gtk+-2.10.0/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/kingfield/Desktop/gtk+-2.10.0/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kingfield/Desktop/gtk+-2.10.0'
make: *** [all] Error 2

```

help please. 
thanks in advance.

---

### Post by Ramses de Norre on 2007-02-23
Seems like you're missing some libraries? Have you got build-essential, libgtk2.0-dev and libgtk-dev installed? Look in the READ_ME and INSTALL files for additional libraries you need.
Is there a configure script? If so: does it finish without errors or "not found"'s on libraries?

---

### Post by Kingfield on 2007-02-23
as i stated - no errors during compile, i will try installing those now

EDIT: both those are already latest version...

---

### Post by Kingfield on 2007-02-23
Bump please help....

---

### Post by GoingDown on 2007-02-23
The error messages you have sent is too short - actual error message should be somewhere earlier.

Can you post a little bit longer error report, from first ERROR statement you can find?

---

### Post by Kingfield on 2007-02-23
I think thats the only error msg... but i'll post a bit before that as wel.

```
make[4]: Entering directory `/home/kingfield/Desktop/gtk+-2.10.0/gtk'
/bin/sh ../libtool --mode=link gcc  -DG_DISABLE_DEPRECATED -g -O2 -Wall   -o gtk-query-immodules-2.0  queryimmodules.o libgtk-x11-2.0.la ../gdk-pixbuf/libgdk_pixbuf-2.0.la ../gdk/libgdk-x11-2.0.la
gcc -DG_DISABLE_DEPRECATED -g -O2 -Wall -o .libs/gtk-query-immodules-2.0 queryimmodules.o  ./.libs/libgtk-x11-2.0.so -L/usr/local/lib /home/kingfield/Desktop/gtk+-2.10.0/gdk/.libs/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so ../gdk-pixbuf/.libs/libgdk_pixbuf-2.0.so ../gdk/.libs/libgdk-x11-2.0.so /usr/lib/libpangocairo-1.0.so /usr/lib/libcairo.so /usr/lib/libpangoft2-1.0.so /usr/lib/libpango-1.0.so /usr/local/lib/libpango-1.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so /usr/local/lib/libcairo.so /usr/lib/libfreetype.so -lz -lpng12 -lfontconfig -lXext -lXrender -lX11 -lXinerama -lXrandr -lXcursor -lXfixes /home/kingfield/Desktop/gtk+-2.10.0/gdk-pixbuf/.libs/libgdk_pixbuf-2.0.so /usr/local/lib/libgmodule-2.0.so -ldl /usr/local/lib/libgobject-2.0.so /usr/local/lib/libglib-2.0.so -lm
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_title'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_is_private'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_description'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_free'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_type_register_static_simple'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_create'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_surface_set_fallback_resolution'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_load_from_file'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_visited'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_modified'./.libs/libgtk-x11-2.0.so: undefined reference to `g_key_file_set_double'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_mime_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_is_private'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_has_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_key_file_get_double'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_applications'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_ps_surface_set_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_uris'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_new'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_description'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_title'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_surface_get_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_to_file'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_group'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_create_for_stream'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_application'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_remove_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_mime_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_move_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_set_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_groups'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_app_info'./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_added'
collect2: ld returned 1 exit status
make[4]: *** [gtk-query-immodules-2.0] Error 1
make[4]: Leaving directory `/home/kingfield/Desktop/gtk+-2.10.0/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/kingfield/Desktop/gtk+-2.10.0/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/kingfield/Desktop/gtk+-2.10.0/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kingfield/Desktop/gtk+-2.10.0'
make: *** [all] Error 2

```

---

### Post by po0f on 2007-02-23
Kingfield,

Why are you compiling GTK from source?  Are you running Dapper and need GTK 2.10?  It would probably be a lot easier to upgrade to Edgy.  GTK is a pretty important library.

[EDIT]

I noticed in the make output that you are still using the default glib.  If you really want to do this, you might have to custom compile glib as well.

[EDIT2]

Is /usr/local/lib in /etc/ld.so.conf?  If not add it, and run `sudo ldconfig` to update ld.so's cache.  If it is, did you run `sudo ldconfig` to update ld.so's cache?  :)

---

### Post by Kingfield on 2007-02-23
yes the ld.conf part, but i have already installed latest glib... and the reason i am doing this is because my file roller does not work, the file chooser has error message about GTK_IS_FILE_CHOOSER failed, or somethin.

```
(file-roller:5207): libglade-WARNING **: unknown widget class 'GtkFileChooserButton'

(file-roller:5207): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkFileChooser'

(file-roller:5207): Gtk-CRITICAL **: gtk_file_chooser_set_current_folder: assertion `GTK_IS_FILE_CHOOSER (chooser)' failed
```

there, if you can help me solve that problem maybe then  i wont need to install it...

---

### Post by po0f on 2007-02-23
Kingfield,

Well, have you filed a bug on [Launchpad](http://launchpad.net/ubuntu) for it?

---

### Post by Kingfield on 2007-02-23
no... i was hoping someone could help me... or could someone give a .deb?

---

### Post by Tomosaur on 2007-02-23
Did you run ./configure before you did make? Configure should throw up any pre-compilation issues.

---

### Post by Kingfield on 2007-02-23
i solved this error... but now i have this... :
with alacarte... 

```
kingfield@kingfield-desktop:~/Desktop/libglade-2.6.0$ alacarte

(alacarte:23773): libglade-WARNING **: could not find `gnome' init function: `glade_module_register_widgets': /usr/lib/libgnome.so: undefined symbol: glade_module_register_widgets

(alacarte:23773): libglade-WARNING **: could not find `bonobo' init function: `glade_module_register_widgets': /usr/lib/libbonobo.so: undefined symbol: glade_module_register_widgets

(alacarte:23773): libglade-WARNING **: unknown property `enable_layout_config' for class `GnomeApp'

(alacarte:23773): libglade-WARNING **: could not find a parent that handles internal children for `dock'

(alacarte:23773): libglade-WARNING **: could not find a parent that handles internal children for `appbar'

(alacarte:23773): libglade-WARNING **: unknown property `max_saved' for class `GnomeIconEntry'

(alacarte:23773): libglade-WARNING **: unknown property `max_saved' for class `GnomeFileEntry'

(alacarte:23773): libglade-WARNING **: could not find a parent that handles internal children for `entry'

(alacarte:23773): libglade-WARNING **: unknown property `max_saved' for class `GnomeIconEntry'

(alacarte:23773): libglade-WARNING **: unknown property `max_saved' for class `GnomeIconEntry'

(alacarte:23773): libglade-WARNING **: unknown property `max_saved' for class `GnomeIconEntry'

(alacarte:23773): libglade-WARNING **: unknown property `max_saved' for class `GnomeFileEntry'

(alacarte:23773): libglade-WARNING **: could not find a parent that handles internal children for `entry'
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 26, in ?
    main()
  File "/usr/bin/alacarte", line 23, in main
    GnomeFront()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 57, in __init__
    self.tree.get_widget('editproperties').set_sensitive(False)
AttributeError: 'NoneType' object has no attribute 'set_sensitive'
kingfield@kingfield-desktop:~/Desktop/libglade-2.6.0$ file-roller
kingfield@kingfield-desktop:~/Desktop/libglade-2.6.0$ alacarte

(alacarte:23897): libglade-WARNING **: could not find `gnome' init function: `glade_module_register_widgets': /usr/lib/libgnome.so: undefined symbol: glade_module_register_widgets

(alacarte:23897): libglade-WARNING **: could not find `bonobo' init function: `glade_module_register_widgets': /usr/lib/libbonobo.so: undefined symbol: glade_module_register_widgets

(alacarte:23897): libglade-WARNING **: unknown property `enable_layout_config' for class `GnomeApp'

(alacarte:23897): libglade-WARNING **: could not find a parent that handles internal children for `dock'

(alacarte:23897): libglade-WARNING **: could not find a parent that handles internal children for `appbar'

(alacarte:23897): libglade-WARNING **: unknown property `max_saved' for class `GnomeIconEntry'

(alacarte:23897): libglade-WARNING **: unknown property `max_saved' for class `GnomeFileEntry'

(alacarte:23897): libglade-WARNING **: could not find a parent that handles internal children for `entry'

(alacarte:23897): libglade-WARNING **: unknown property `max_saved' for class `GnomeIconEntry'

(alacarte:23897): libglade-WARNING **: unknown property `max_saved' for class `GnomeIconEntry'

(alacarte:23897): libglade-WARNING **: unknown property `max_saved' for class `GnomeIconEntry'

(alacarte:23897): libglade-WARNING **: unknown property `max_saved' for class `GnomeFileEntry'

(alacarte:23897): libglade-WARNING **: could not find a parent that handles internal children for `entry'
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 26, in ?
    main()
  File "/usr/bin/alacarte", line 23, in main
    GnomeFront()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 57, in __init__
    self.tree.get_widget('editproperties').set_sensitive(False)
AttributeError: 'NoneType' object has no attribute 'set_sensitive'
kingfield@kingfield-desktop:~/Desktop/libglade-2.6.0$


```

any suggestions?

---

### Post by Kingfield on 2007-02-23
> **Tomosaur said:**
> Did you run ./configure before you did make? Configure should throw up any pre-compilation issues.

no pre-compilation issues.

---

### Post by redkazuo on 2007-04-01
I had this same issue on my slackware system. Although I don't actually know what I'm doing, configuring everything with --prefix=/usr got me through this nightmare.

It seemed as though libtool would have to be properly (de)configured if I wanted to have a new version of glib-2.0 on /usr/local as I was previously trying to.

Discussion on this problem is rather scarce on google, too. I wonder why that is. Perhaps the only people who try to compile a huge program like gtk are the ones who really really know what they're doing. I have to admit most of the time I just poke my linux troubles until they go away... hahaha...

Anyhow, I hope you figure this all out soon enough as well.

---

### Post by Kingfield on 2007-04-30
Heh.. sorry to bring back an old topic like this... but this problem is really bugging me.. are there any solutions?

---

### Post by tbartcz on 2008-02-16
Hi,
I have come across the same error and I would like to share the solution with you. When I started the configure script of GTK+ first time it complained that my Glib library was too old. Therefore I downloaded newer version, compiled and installed it. After that GTK+ configure script executed without any problems. 
GTK+ compilation was also successful however the problem started on linking stage where I got similar errors like mentioned in this thread, for example:
libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_description'

I figured out that missing symbols came from Glib library. I was surprised because my newer of this library version definitely supported the mentioned symbols. So I came to the conclusions that there had to be used some older version of Glib library. I have checked that and it turned out that in directory /opt/gnome/lib were older versions of Glib library which were taken by the build process. Once I corrected that I successfully build GTK+. 
Regards
Tom

---

### Post by Mark76 on 2008-02-17
Can anyone tell me why I get this error when I try to comile gtk+-2.12.6

> checking for XOpenDisplay... no
configure: error: *** libX11 not found. Check 'config.log' for more details.

I know I have X11, so why the hell can't the damned program find it?

---

### Post by GoingDown on 2008-02-19
> **Mark76 said:**
> I know I have X11, so why the hell can't the damned program find it?

Do you have libx11-dev installed?

---

### Post by Mark76 on 2008-02-19
Yep. Present and correct.

---

