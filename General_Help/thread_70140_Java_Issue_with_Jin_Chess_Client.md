---
title: "Java Issue with Jin Chess Client"
date: 2005-09-29
forum: General Help
---

### Post by rlklee on 2005-09-29
When I try to launch Jin, I get this output in the console before the crash:

---

rylklee@ryanbox:~/tars/jin-2.13.1$ ./jin
(.:10563): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed
** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
./jin: line 14: 10563 Aborted                 java $JAVA_OPTS -jar jin.jar $*

---

Does anyone have any idea?

I am running Breezy's latest colony release, and have already posted on the development forum, but my question received no reply.  In any case, I suspect that it isn't a "breezy" problem anyhow, as it existed before I upgraded from Hoary.  (Neither do I think that this problem is one with Jin).

---

