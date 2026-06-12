---
title: "Cann't login after install openoffice word processor in ubuntu"
date: 2008-02-13
forum: General Help
---

### Post by yinglcs2 on 2008-02-13
Hi,

I can't login after install openoffice word processor in ubuntu 7.10.

I end up login in a fail-safe session. And this is what I get in .xsession-errors.

Can you please tell me how can I fix my problem?

$ more .xsession-errors 
gdm[5806]: DEBUG: Attempting to parse key string: daemon/Greeter=/usr/lib/gdm/gd
mlogin
gdm[5806]: DEBUG: Attempting to parse key string: daemon/PreSessionScriptDir=/et
c/gdm/PreSession/
gdm[5806]: DEBUG: Forking extra process: /etc/gdm/PreSession/Default
gdm[5807]: DEBUG: Attempting to parse key string: xdmcp/Enable=false
gdm[5807]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gd
m
gdm[5807]: DEBUG: Attempting to parse key string: daemon/RootPath=/sbin:/usr/sbi
n:/bin:/usr/bin

(process:5809): Gtk-WARNING **: This process is currently running setuid or setg
id.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5813): Gtk-WARNING **: This process is currently running setuid or setg
id.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
gdm[5806]: DEBUG: Attempting to parse key string: daemon/DefaultPath=/bin:/usr/b
in
gdm[5806]: DEBUG: Attempting to parse key string: daemon/BaseXsession=/etc/gdm/X
session
gdm[5806]: DEBUG: Running /etc/gdm/Xsession /usr/local/bin/startxgl.sh for scheu
ng on :0
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -
fullscreen -br +xinerama 
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixin
g.
/usr/bin/ssh-agent: error while loading shared libraries: libgssapi_krb5.so.2: c
annot open shared object file: Input/output error

---

