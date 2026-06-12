---
title: "Odd error preventing loading of Gnome desktop"
date: 2007-05-08
forum: General Help
---

### Post by everdred on 2007-05-08
I get the following error when logging in to my Gnome desktop:

> An error occurred while loading or saving configuration information for Encryption Key Agent (Seahorse). Some of your configuration settings may not work properly.

There's a "Details" button below, clicking it reveals the following:

> Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0


After dismissing that window, I can choose to log out or continue anyway. Choosing the continue option doesn't work; it just takes me back to the GDM login screen. This is the same when using Failsafe Gnome.

This is how it happens when trying to sign in to Gnome. Fortunately, I also have Fluxbox available. I get the same error when signing in with Flux, but am at least able to continue to a usable desktop.

I've tried aptitude purging seahorse, and am greeted with the following error:

> Removing seahorse ...
No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'

Failed to load source "xml:readwrite:/var/lib/gconf/defaults": Failed: Couldn't locate backend module for `xml:readwrite:/var/lib/gconf/defaults'

GConf-ERROR **: file gconftool.c: line 892 (main): assertion failed: (err == NULL)
aborting...
dpkg: error processing seahorse (--purge):
 subprocess pre-removal script returned error exit status 250
Errors were encountered while processing:
 seahorse
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Does anyone have any ideas as to what I should try?

---

### Post by abc123456 on 2007-05-08
Try mv .bashrc bashrc.  You can always mv it back.  It took that to fix my kde login.:)

---

### Post by everdred on 2007-05-08
Thanks, abc, but that didn't do it.

I have more details about the errors I'm receiving in Gnome. I couldn't copy and paste these anywhere, so I had to type these manually:

First, I get an error saying something along the lines of > the files that contain your preference settings are currently in use.

It went on to say something about other signed-in sessions. But there are none.

Then, after dismissing that window, I get this:

> please contact your system administrator to resolve the following problem:

could not resolve the address "xml:readonly:/etc/gconf/gconf.xml.mandatory" in the configuration file
"/etc/gconf/2/path": Failed: Couldn't load backend module "xml:readonly./etc/gconf/gconf.xml.mandatory"


---

### Post by everdred on 2007-08-22
Any other ideas? I just had this start happening to another Ubuntu installation that's been perfect for me for months now... though I installed Seahorse last week, and the initial error I'm receiving makes note of Seahorse, so I'm now a bit suspicious of it.

---

