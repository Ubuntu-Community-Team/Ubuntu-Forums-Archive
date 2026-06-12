---
title: "locale madness recovering from crash"
date: 2006-10-09
forum: General Help
---

### Post by MaskedMarauder on 2006-10-09
](*,) 

hi,


over the weekend I had a disk crash.  It was pure hardware and had nothing to do with ubuntu.

But, trying to get things back up from a recent backup, the locales thing has gone haywire.  I've fixed a lot of it, but get two persistent errors I can't make go away and things won't work.


I have about a half dozen applications open and not one of them has a title, just blanks on the titlebar where the name used to be.

when I run ANY gnome application ( don't see this problem with KDE apps) I get:

Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

Thousands of 'em.

Sometimes I see:

(eog:7565): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(eog:7565): GdkPixbuf-CRITICAL **: gdk_pixbuf_set_option: assertion `key != NULL' failed

(eog:7565): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
...etc.



Obviously, some gtk/gdk/gnome/??? library is broken.  

Can somebody tell me which one, or how to find out so I can reinstall/reconfigure it?

I've reinstalled every obviously gtk/gdk/gnome package I can find, but nothting is working.

I did the obvious things with reconfiguring languages, locales and /etc/environment.  That only helped the kde & text-based applications.  I reinstalled libc since, as I understand it, iconv is now part of the basic libc packaage.  

But Gnome is still thoroughly gorked.

Beyond the obvious problem with having to paw through a heap of annonymous windows to find the app I want to work in, there are other problems too.  Evolution won't work anymore because it can't lock files.  As best as I can figure the problem is it tries to locak a file, specified in utf-8, but the process doing the locking can't understand it.  (that's just a guess on my part.)  But there's lots of problems where one app has to communicate with another or, god forbid, work with pix buffers (I reinstalled everyting with pixbuf in their name, description, dependencies or proider fields: no joy).



Is there ANY way to fix this without erasing my main disk and re-installing from scratch?


----------------
A suggestion:

In general terms I think this reveals a problem with (at least) ubuntu.  The locale thing is a keystone component that MUST work.  Yet managing/repairing it is so esoteric that it borders on clandestine opperations.

Applications shouldn't be able to throw thousans of critical errors without there being a more-or-less accessible remedy for typical or even advanced users.  I see a lot of people getting flumoxed over locale weirdnesses here.

Back in the old days with text-based systems, if you screwed up your display you could type 'tty sane' and it would give you a readable terminal again which you could fiddle with again as needed to special formatting.

I think linux/ubuntu needs something like that here so that if it gets buggered up, for whatever reason, some key constellation of packages could be flagged for re-installation/configuration so that at least things work.

---

