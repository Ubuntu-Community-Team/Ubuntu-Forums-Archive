---
title: "Gnome is still hanging about...."
date: 2006-11-09
forum: General Help
---

### Post by civint on 2006-11-09
I followed the instructions to get a fresh install of kde-core, with the dapper removal of all gnome files (as instructed on the psychocats ubuntu tutorial, however, now I am stuck with a single file from the previous install that apparently is neither removed, or removable....

I was attempting to install the Koffice suite of programs, and it told me 
> The following packages will be REMOVED:
  scim-gtk2-immodule


However, after that it printed this 
> Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libgsf-1-common 1.13.99-0ubuntu2 [44.3kB]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libgsf-1-113 1.13.99-0ubuntu2 [121kB]
Fetched 165kB in 0s (199kB/s)
(Reading database ... 77144 files and directories currently installed.)
Removing scim-gtk2-immodule ...
/var/lib/dpkg/info/scim-gtk2-immodule.postrm: line 8: /usr/sbin/update-gtk-immodules: No such file or directory
dpkg: error processing scim-gtk2-immodule (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 scim-gtk2-immodule
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


I have tried simply to remove it using both apt-get and aptitude but I have not been able to remove it.

---

### Post by civint on 2006-11-09
anyone? excuse rudeness, but with this error I cannot install any programs which are neccesary...

---

### Post by PanzerMKZ on 2007-12-26
I am having the same issue with trying to upgrade a 7.04 install to 7.10.  But this /var/lib/dpkg/info/scim-gtk2-immodule.postrm not being found is messing me up.  any fix?



Panzer

---

### Post by monkiki on 2008-06-11
This script is in package libgtk2.0-bin an this is the code:

#!/bin/sh

# this script is a no-op since 2.10.3-2
exit 0

set -e

VERSION="2.12.9"
GTK_BINARY_VERSION="2.10.0"
APIVER="2.0"
SHARED_PKG="libgtk2.0-0"
TMPFILE=$(mktemp -t "gtk+$APIVER-$VERSION.XXXXXXXXXX")

echo -n "Updating the IM modules list for Gtk+ $VERSION..."
"/usr/lib/$SHARED_PKG/gtk-query-immodules-$APIVER" \
    $(find "/usr/lib/gtk-$APIVER/$GTK_BINARY_VERSION/immodules" -name '*.so') \
    > "$TMPFILE"
if [ "x`cat "$TMPFILE" | grep -v '^#'`" = "x" ]; then
    echo "no Gtk+ IM modules found."
else
    echo "done."
fi
if ! test -d "/etc/gtk-$APIVER"; then
    echo -n "Creating /etc/gtk-$APIVER..."
    mkdir "/etc/gtk-$APIVER"
    echo "done."
fi
cp "$TMPFILE" "/etc/gtk-$APIVER/gtk.immodules"
chmod 644 "/etc/gtk-$APIVER/gtk.immodules"

rm -f "$TMPFILE"

---

