---
title: "Firefox crashes after any download"
date: 2007-06-02
forum: General Help
---

### Post by loweb1 on 2007-06-02
Hi, I'm using Firefox 2.0.0.4 and I do have a few add-ons installed however I haven't added any new ones for quite sometime. 

I'm pretty sure this started right after I upgraded to 2.0.0.4 from 2.0.0.3 via the automatic updates Ubuntu says I need. 

It doesn't matter what it is I try to download (even right clicking on a photo for "Save image as"), the download dialog will appear just fine and I'll start downloading, and as soon as the download is finished firefox just shuts itself down. 

I was using the download status bar add-on but disabling it makes no difference, firefox will crash after downloads regardless of the download manager. 

I'd appreciate any idea's. I suppose I should post a similar thread in a firefox help forum too. 

Here's the line from the firefox about dialog:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)

---

### Post by loweb1 on 2007-06-02
Well I fixed it sort of. I ended up completely removing and then reinstalling firefox. Not the best solution but it seems to have worked, now I just have to set it all back up the way I liked it again.

---

### Post by loweb1 on 2007-07-21
Yes, I'm replying to myself. Again.

I just got an auto upgrade from 2.0.0.4 to 2.0.0.5 and the exact same thing started happening all over again. 

I'm going to reinstall now and see if that works but really, Am I going to have to do this every time?!

---

### Post by dogeatery on 2008-05-28
I'm having this exact same problem with Firefox 3 RC 1 in Linux Mint Elyssa.  As soon as things finish downloading, it's as though they execute a kill command!  I ran $firefox and the printout is below (the second printout may be for gdebi installer that opened immediately as firefox crashed):

```
dogeatery@dogeatery-laptop ~ $ firefox
CI: {44cc2b80-ac35-4428-9dd1-13c1cf2dfc87}
Segmentation fault
dogeatery@dogeatery-laptop ~ $ /usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.5/site-packages/GDebi/GDebi.py:93: GtkWarning: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed
  self.window_main.set_sensitive(False)
```

anybody have any ideas?

---

### Post by anupkshah on 2008-06-03
Hi,

I was having similar problems with Firefox 3 RC 1.

I found that it was because I had the Prism extension (2.0 I think?).

I found this out by disabling all my extensions and enabling them one by one (or in small groups) and downloading some small file until it stopped crashing on download.

It might be that there are some other extensions that cause this problem too, or that disabling/uninstalling was more important...

Hope that helps.

---

