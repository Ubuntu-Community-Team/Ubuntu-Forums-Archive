---
title: "pan newsreader error interpreting jpeg"
date: 2007-12-25
forum: General Help
---

### Post by rockrhino27 on 2007-12-25
Hi all, 

     Anyone run into an issue viewing multi part jpeg files in pan newsreader?  I was downloading jpeg files the other day running Ubuntu Gutsy and with a multi part jpeg file I only get the first third of it.  The rest of the file is either black or filled with garbage lines.  I read somewhere that it had to do with libgtk2, but replacing it would brake a dozen other applications.  I do get an error within pan when it tries to read a multi part jpeg stating, "Error Interpreting JPEG image file (Application Transferred Too Few Scanlines)".  

Anybody run into a similar issue?  

Please let me know.  

Thanks all, 

Rich

---

### Post by rockrhino27 on 2007-12-30
bumping myself.  Please help.

---

### Post by jromer on 2007-12-30
I ended up going back to the last stable release...


Here's a link for a .deb for dapper of pan version 0.14.2.. I've been using it on Gutsy without any problems.

(scroll to bottom of page)
[http://packages.ubuntu.com/dapper/news/pan](http://packages.ubuntu.com/dapper/news/pan)

edited: I've since been using the version supplied with Gutsy and like it very much.

---

### Post by rockrhino27 on 2008-01-05
No Love.  Thanks for the suggestion.  It worked just fine in Feisty, and I just tried downgrading to the feisty distro and I get the same result....   

Anybody else experiencing this?  I guess not that many people use newsgroups anymore?

---

### Post by paradog on 2008-01-06
I had the same problem when upgrading to Gutsy a couple of weeks ago, and also wanted to avoid having to upgrade gtk. If you're up for recompiling Pan, there's a patch you can apply gui/body-pane.cc:
---------------------------------------------------
$ diff -U 7 body-pane.cc.ORIGINAL body-pane.cc
--- body-pane.cc.ORIGINAL    2007-12-28 17:33:37.000000000 -0800
+++ body-pane.cc        2007-12-28 17:36:48.000000000 -0800
@@ -811,16 +811,24 @@
     // populate the loader
     GMimeDataWrapper * wrapper (g_mime_part_get_content_object (part));
     if (wrapper)
     {
       GMimeStream * mem_stream (g_mime_stream_mem_new ());
       g_mime_data_wrapper_write_to_stream (wrapper, mem_stream);
       GByteArray * buffer (GMIME_STREAM_MEM(mem_stream)->buffer);
-      if (buffer->len)
-          gdk_pixbuf_loader_write (l, (guchar*)buffer->data, buffer->len, &err);
+
+      size_t c = 0;
+      size_t left = buffer->len;
+      while (left > 0)
+      {
+        size_t len = left < 1024 ? left : 1024; /* KLUDGE magic number */
+        gdk_pixbuf_loader_write (l, ((guchar*)buffer->data) + c, len, &err);
+        left -= len;
+        c += len;
+      }
       g_object_unref (mem_stream);
       g_object_unref (wrapper);
     }
   
     // create the pixbuf
     GdkPixbuf * pixbuf (0);
     if (!err)

-------------------------------------------------
(this is for the 0.132 source code)

Unfortunately, recompiling Pan will require an upgrade to two other libraries:  gmime (to 2.2.12) and libpcre (to pcre-5.0),  which I also had to compile from source.  And some library links don't get created on install, so you'll have to relink them.    

If you can't recompile, you might submit a bug report to the development team...

---

### Post by ArcherB on 2008-01-08
Will that patch fix the issue?  If so, how do I apply  it?  

There is also a bug report filed.  [http://bugzilla.gnome.org/show_bug.cgi?id=495722](http://bugzilla.gnome.org/show_bug.cgi?id=495722)

If your patch fixes this, I'm sure they'd like to know about it.

Thanx!

**EDIT**

Never mind.  I figured it out.  Remove the lines with - in front of them.  Add the lines with the + in front of them in place of the lines you just removed.  Recompile.

And, it works!

Awesome, and thanks again!

---

### Post by paradog on 2008-01-09
Glad it worked out!  I can't take credit for the code, though.  I found it somewhere and can't locate the original.

---

