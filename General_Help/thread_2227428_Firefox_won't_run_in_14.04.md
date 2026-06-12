---
title: "Firefox won't run in 14.04"
date: 2014-06-02
forum: General Help
---

### Post by duelistjp on 2014-06-02
I just installed ubuntu 14.04 yesterday and while I've been working on a few problems including brightness and hibernation i've liked what i've seen.  However today I am unable to launch firefox i get the spinning mouse but nothing happens.  I am however able to launch ff in the guest session.  When I launch by terminal I get the following errors

(process:6382): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(firefox:6382): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(firefox:6382): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(firefox:6382): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(firefox:6382): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
Could not create gnome accelerators directory `/home/USERNAME_REMOVED/.gnome2/accels': Permission denied

I have tried deleting .mozilla but it doesn't seem to help  I am however able to run ff if i use gksudo.  Any ideas on how to get this working properly?

---

### Post by ajgreeny on 2014-06-02
NEVER use firefox or any other application facing the internet as root; it is far too dangerous an activity to do that.

This seems to be a related to FF which has been noted at [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1278062](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1278062) but more in Lubuntu than Ubuntu, as far as I'm aware.  Have you fully updated your system after installing, and are you using unity or some other DE?

---

### Post by duelistjp on 2014-06-02
I know that but thought the risk of accessing the mozilla start page as root was worth seeing if it launched. I am using chrome for my general browsing.  The link you gave was informative.  I found something that seems to work but I'm not sure if it will end up screwing things up later on.  I used chown to take control of the .gnome directory in my profile.  should this cause any problems?

---

### Post by ajgreeny on 2014-06-02
That .gnome folder should be yours in the first place and assuming you changed ownership to yourself all is well. Everything else in your home should also belong to you, so if that is what you mean in your post, all should be good.

---

### Post by duelistjp on 2014-06-02
well i guess it's solved then although I screwed up some stuff while trying to get hibernating and had to reinstall without lvm to get it working.  Thanks for helping me though

---

