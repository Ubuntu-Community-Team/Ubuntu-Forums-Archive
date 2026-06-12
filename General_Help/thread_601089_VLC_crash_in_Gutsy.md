---
title: "VLC crash in Gutsy"
date: 2007-11-02
forum: General Help
---

### Post by billstei on 2007-11-02
What's this all about?

$ wxvlc
VLC media player 0.8.6c Janus
*** glibc detected *** wxvlc: free(): invalid pointer: 0x083d4310 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c4ed65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7c52800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb6b6d961]
/usr/lib/libwx_gtk2u_core-2.6.so.0[0xb74e4950]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN8wxButton10SetDefaultEv+0x76)[0xb74e4a36]
/usr/lib/vlc/gui/libwxwidgets_plugin.so(_ZN5wxvlc8MessagesC1EP13intf_thread_tP8wxWindow+0x5b4)[0xb79676c4]

---

### Post by billstei on 2007-11-02
Getting an almost identical crash in Audacity, so it must be a wxWidgets problem.

---

### Post by billstei on 2007-11-02
Uninstalled all wx 2.6 packages along with vlc, wxvlc, and audacity.  Reinstalled them.  OK now.

---

### Post by rocksocke on 2007-11-04
Hi!

i think i have a similar problem:

```

$ wxvlc
VLC media player 0.8.6c Janus
[00000293] main interface error: no suitable interface module
[00000001] main private error: interface "(null)" initialization failed

```

which packages exactly have you removed?

thanks!

---

### Post by billstei on 2007-11-06
That sounds like a plugin problem, ie an "interface module".  There is nothing in that error message to suggest that wx is the problem.

Here is a very similar post: [http://ubuntuforums.org/showthread.php?t=402905](http://ubuntuforums.org/showthread.php?t=402905)

You could also try searching or posting for help on the vlc forum: [http://forum.videolan.org/index.php](http://forum.videolan.org/index.php)

Bill

---

### Post by rocksocke on 2007-11-18
Thanks for your reply.

Unfortunately reeinstalling didn't solve the problem.

But! Removing local VLC-information did the thing. i think it was a problem with upgrading and keeping old configuration files.

```

rock@socke:~$ cd
rock@socke:~$ rm -rf .vlc/

```

after that it worked again.

but nevertheless i had another bigger problem. as i installed imagemagick 5.8 to work with php4 (wich i compiled myself too) i didn't came arround compiling my own libpng12 wich i placed in /usr/local/lib - well this was the problem, ldconfig took my own not the one located in /usr/lib - for that reason many applications including vlc didn't work. til now - i moved my own compiled version to a not standard-path, did ldconfig and now everything works again.

strange - or better to say: logical - how things are connected.

---

