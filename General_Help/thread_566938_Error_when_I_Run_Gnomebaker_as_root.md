---
title: "Error when I Run Gnomebaker as root"
date: 2007-10-04
forum: General Help
---

### Post by geoffBEAM on 2007-10-04
So I have been trying to burn a CD with various utilities, and I finally read some advice somehwere to run gnomebaker as root. What follows is the error I get from the terminal

> home@home-desktop:~$ sudo gnomebaker

(process:5527): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


Can anyone help? In every app the file preperation works but the burn process never starts and the drive never lights up!

Thanks in advance!

---

### Post by renzokuken on 2007-10-04
why are you running gnomebaker as root? you shouldnt need to

---

### Post by geoffBEAM on 2007-10-04
I can't burn cd's, and some1 suggested it.

---

### Post by zvacet on 2007-10-04
Try to reinstall it in synaptic.If that doesn´t help,install k3b.You will have even more options with it.

---

### Post by Pygi on 2007-10-05
You appear to be using the older version of Gnomebaker. Please try to use Gnomebaker 0.6.2.
With cdrkit you shouldn't need to run it as root, while with cdrtools you will have to.

Kind regards,
M.

---

