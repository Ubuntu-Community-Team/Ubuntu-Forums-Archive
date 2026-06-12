---
title: "Correct locations for Firefox plugins with 3.0b5?"
date: 2008-05-27
forum: General Help
---

### Post by jdpipe on 2008-05-27
Hi there

What is the current correct location for firefox plugins in Ubuntu Hardy?

I have installed the 'tiff-plugin' package distributed from outside the Ubuntu repositories, but it doesn't work, perhaps installed to the wrong location?

[http://tiff-plugin.sourceforge.net/](http://tiff-plugin.sourceforge.net/)

Cheers
JP

john@thunder:~$ dpkg -L mozilla-tiff-plugin
/.
/debian-binary
/usr
/usr/lib
/usr/lib/mozilla-firefox
/usr/lib/mozilla-firefox/plugins
/usr/lib/mozilla
/usr/lib/mozilla/plugins
/usr/lib/firefox
/usr/lib/firefox/plugins
/usr/lib/mozilla-tiff-plugin
/usr/lib/mozilla-tiff-plugin/mozilla-tiff-plugin.so
/usr/lib/mozilla-snapshot
/usr/lib/mozilla-snapshot/plugins
/usr/share
/usr/share/doc
/usr/share/doc/mozilla-tiff-plugin
/usr/share/doc/mozilla-tiff-plugin/README.SUSE
/usr/share/doc/mozilla-tiff-plugin/README
/usr/share/doc/mozilla-tiff-plugin/AUTHORS
/usr/bin
/usr/bin/mozilla-tiff-viewer
/usr/lib/mozilla-firefox/plugins/mozilla-tiff-plugin.so
/usr/lib/mozilla/plugins/mozilla-tiff-plugin.so
/usr/lib/firefox/plugins/mozilla-tiff-plugin.so
/usr/lib/mozilla-snapshot/plugins/mozilla-tiff-plugin.so

---

### Post by zenwalker on 2008-05-28
Well if u can find /usr/lib/firefox dir, then yes it has installed inside it correctly, but make sure u r using correct versions req.

---

### Post by jdpipe on 2008-05-28
But what is the correct location?

I have files in various places. What is the location that firefox-3.0b5 uses?

This system is an upgrade from Ubuntu 6.10 originally, so there's no guarantee that just because /usr/lib/firefox exists that it's the current plugin location.

[edit] For example...

john@thunder:~$ /usr/lib/firefox [tab]
firefox/        firefox-3.0b5/  firefox-addons/ 
john@thunder:~$ /usr/lib/mozilla [tab]
mozilla/             mozilla-snapshot/    
mozilla-firefox/     mozilla-tiff-plugin/ 
john@thunder:~$ /usr/lib/mozilla

---

### Post by Bubba64 on 2008-05-28
> **jdpipe said:**
> Hi there

What is the current correct location for firefox plugins in Ubuntu Hardy?

I have installed the 'tiff-plugin' package distributed from outside the Ubuntu repositories, but it doesn't work, perhaps installed to the wrong location?

[http://tiff-plugin.sourceforge.net/](http://tiff-plugin.sourceforge.net/)

Cheers
JP

john@thunder:~$ dpkg -L mozilla-tiff-plugin
/.
/debian-binary
/usr
/usr/lib
/usr/lib/mozilla-firefox
/usr/lib/mozilla-firefox/plugins
/usr/lib/mozilla
/usr/lib/mozilla/plugins
/usr/lib/firefox
/usr/lib/firefox/plugins
/usr/lib/mozilla-tiff-plugin
/usr/lib/mozilla-tiff-plugin/mozilla-tiff-plugin.so
/usr/lib/mozilla-snapshot
/usr/lib/mozilla-snapshot/plugins
/usr/share
/usr/share/doc
/usr/share/doc/mozilla-tiff-plugin
/usr/share/doc/mozilla-tiff-plugin/README.SUSE
/usr/share/doc/mozilla-tiff-plugin/README
/usr/share/doc/mozilla-tiff-plugin/AUTHORS
/usr/bin
/usr/bin/mozilla-tiff-viewer
/usr/lib/mozilla-firefox/plugins/mozilla-tiff-plugin.so
/usr/lib/mozilla/plugins/mozilla-tiff-plugin.so
/usr/lib/firefox/plugins/mozilla-tiff-plugin.so
/usr/lib/mozilla-snapshot/plugins/mozilla-tiff-plugin.so

If you open add ons in tools and click on plugins it will show you what is there. This does not fix your problem completely but may help

---

### Post by jdpipe on 2008-05-28
This is not an answer to my question. But it does appear that *a* correct location for Firefox plugins on Hardy is

/usr/lib/xulrunner-addons/plugins

With tiff-plugin, I was able to make use of the .deb package hosted at [http://tiff-plugin.sf.net/](http://tiff-plugin.sf.net/) using the following commands:

 cd /usr/lib/xulrunner-addons/plugins/
 sudo ln -s /usr/lib/firefox/plugins/mozilla-tiff-plugin.so libtiff-plugin.so

I don't know if this is the 'preferred' plugin location, or not, however.

Note that there is also a directory called:
/usr/lib/firefox-3.0b5/plugins

But I don't know to what extent we are supposed to use that dir.

---

