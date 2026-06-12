---
title: "Compiling MusicTracker"
date: 2007-07-04
forum: General Help
---

### Post by schwieb on 2007-07-04
Ok, I may be the only person having this problem, as I see lots of posts from people who have successfully compiled this program.  I simply can't manage it.  I have installed what I believe are the necessary libraries, but it still will not get past the configure stage.  

When i try to do a configure, I get eh following dbus error:

checking for DBUS... configure: error:
*** DBUS 0.62+ is required to build MusicTracker; please make sure you have the
*** DBUS development files installed. The latest version of DBUS is always
*** available at [http://dbus.freedesktop.net/](http://dbus.freedesktop.net/).

I have installed dbus and the dbus libraries, and still no avail.  Anyone got any suggestions for me?

---

### Post by vicantre on 2007-07-08
> **schwieb said:**
> Ok, I may be the only person having this problem, as I see lots of posts from people who have successfully compiled this program.  I simply can't manage it.  I have installed what I believe are the necessary libraries, but it still will not get past the configure stage.  

When i try to do a configure, I get eh following dbus error:

checking for DBUS... configure: error:
*** DBUS 0.62+ is required to build MusicTracker; please make sure you have the
*** DBUS development files installed. The latest version of DBUS is always
*** available at [http://dbus.freedesktop.net/](http://dbus.freedesktop.net/).

I have installed dbus and the dbus libraries, and still no avail.  Anyone got any suggestions for me?

Be sure you installed the development libraries of dbus  (those with '-dev' at the end).

---

### Post by schwieb on 2007-07-08
Thanks for the suggestion, but I have installed the pidgin dev package and the gtk dev packages.  I really don't get it.  Is there a way to test if dbus is working properly, and then if so can I pass the path to dbus when compiling?

---

### Post by bryan986 on 2007-08-22
Install libdbus-glib-1-dev

---

### Post by schwieb on 2007-09-10
You are a genius!  That was what I needed!

---

### Post by thulium_168 on 2007-10-11
I'm using dapper and the latest version libdbus-glib-1-dev on the repos is only .60 so I still can't compile. Is there a way to install .62+ version of dbus on dapper? thanks in advance.

---

### Post by jakethecake on 2008-02-02
[http://packages.ubuntu.com/hardy/net/pidgin-musictracker](http://packages.ubuntu.com/hardy/net/pidgin-musictracker)

It will be included in hardy. All of the dependencies are listed.

I just installed libpcre3 on gutsy/7.10 and it compiled fine.

---

### Post by Musashi on 2008-02-04
I'm using musictraker now, on nick config on account config the music name shows fine, but on the window  my nick isn't updated, why?

I'm using the latest plugin and Pidgin 2.3.1

PS: Nevermind, I had a local nick on my account, working fine now. :P

---

