---
title: "wallpaper-tray crashing, help!"
date: 2007-05-03
forum: General Help
---

### Post by gotonpo on 2007-05-03
I did a quick search and didn't find anything, so I hope this hasn't already been answered..

So with the upgrade to Feisty, I got wallpaper-tray to work!  It wouldn't work at all in Edgy.  In fact, the only wallpaper randomizer I got to work is bgchanger.  bgchanger was nice and all, but every time I'd log in it would suck up 100% of my cpu for about 10 minutes.  I guess it was caching my photo collection or something.

wallpaper-tray works quickly and easily and doesn't seem to ever hog my cpu.  The only thing is that it just shuts itself down randomly!  I haven't been able to determine how long it takes for this to happen, but more than 30 minutes, at least.  I currently have it set to change the wallpaper every minute, so I can monitor how well it's working.

I have given it a shot both with and without the "Follow Symlinks" option enabled.  It crashed no matter what.

Can anyone point me to a log file or something that'll say why it crashed?  Or just help me stop it from crashing?

I'd be so grateful!

Thanks..

---

### Post by gotonpo on 2007-05-03
Ok, I spent a good two hours actually doing things.. and wallpaper-tray never hiccuped.

Almost as soon as I left the computer idle, it decided to close itself.

I am very confused.  I turned my energy saving settings to Never turn off anything.  Any other ideas?

I challenge you!  How can this be explained??

---

### Post by sv452 on 2007-05-04
i don't know about feisty but after about two months of struggling i got wp_tray to work on edgy ... and to be honest it was a very simple solution - maybe not the right way but it worked for me ... after solving my dependencies and using the correct ./config operators i got it compiled and installed perfectly and yet it never wanted to work nor did it even show up in my panel aplet list .... so i had this brilliant idea ... check permissions ... and i set it with suid and now it workd flawlessly on both my edgy machines....

what version did u compile? 0.5.3 ?? or the one from synaptic ?

---

### Post by gotonpo on 2007-05-04
I installed the one in the repositories.  Not sure what version that is.. but It's not in the panel applet list, it's under Applications/Graphics.

I'll try installing a newer version from source tonight after work.. thanks for your input!

Do you remember what ./config operators you used?

---

### Post by gotonpo on 2007-05-04
Update:

Ok, the install from source went well.  I figured out the ./configure operators and had all the dependencies installed.

I cannot add it to my gnome panel, just like you, sv452

I tried "sudo chown me:me /usr/local/libexec/wp_tray"

relogged.. still can't add it.

Would you tell me how you used suid to fix this?  Or anyone?

Thanks again!

---

### Post by sv452 on 2007-05-07
hi - ok - u presume u compiled 0.5.3 ...

just for the record i did all in root and not sudo ...

here is a quick step by step ...

my ./config:
```
./configure --prefix=/usr --with-boostfilesystem=/usr/lib/libboost_filesystem.so --with-boostregex=/usr/lib/libboost_regex.so
```

sorted the dependencies.

then i did
```
make && make install
```

then while in terminal under root:
```
nautilus
```

and navigated to /usr/libexec

right click on wp_tray and enabled suid or allow execute - can't remember exactly ...

chmod 755 /usr/libexec/wp_tray

best thing to do is remove the install and recompile with the said ./configure options...

hope this helps ....

---

### Post by olejorgen on 2007-05-08
I must say, that it's really annoying when packages from the repos doesn't work. (Yeah, I know wp-tray isn't officially supported)

---

### Post by sv452 on 2007-05-08
it is annoying - but at least it is not life and death app ... so it can be overlooked ...

and it is rather fun being able to compile an app urself ... :D

---

### Post by gotonpo on 2007-07-04
I hate to resurrect an old thread here, but I finally got this working.  I did a clean install of Feisty and was able to build this from source.  It works, yay!

Although the applet is working fine, it has one major annoyance.  Every time it's about to change the wallpaper I get a gnome notification "Wallpaper tray is about to change your wallpaper.  Do you want to accept this wallpaper?"

It's driving me crazy!  How can I stop this??

Any help is greatly appreciated..

---

### Post by fred.warren on 2007-08-11
The applet is set up to display the change picture or delete picture confirmation under several circumstances. The quick fix, is in the code chage

SetRandom(false);

to read

SetRandom(true);

then compile and install wp_tray. At that point there will be no more confirmations.

---

### Post by DeusEx on 2007-09-23
*BUMP*

I have the random crash too with the repository version.
It also appears after clicking through several wallpapers.

Backtrace:
```


*** glibc detected *** wallpaper-tray: malloc(): memory corruption: 0x081cba68 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb72e2ef3]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb72e460e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb73f12c6]
/usr/lib/libglib-2.0.so.0(g_strdup+0x39)[0xb7404879]
/usr/lib/libgconf-2.so.4(gconf_value_set_string+0x1d)[0xb7d3c82d]
/usr/lib/libgconf-2.so.4(gconf_engine_set_string+0xa1)[0xb7d42b21]
/usr/lib/libgconf-2.so.4(gconf_client_set_string+0xa9)[0xb7d46369]
wallpaper-tray(f_set_rand_wallpaper+0x234)[0x804ee14]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb7a7f6b0]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb746262b]
/usr/lib/libgobject-2.0.so.0[0xb7473103]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb74743ef]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb74747e9]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b93e18]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x183)[0xb7a789c3]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x317)[0xb7a79bc7]
/usr/lib/libgdk-x11-2.0.so.0[0xb77de12a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb73e9df2]
/usr/lib/libglib-2.0.so.0[0xb73ecdcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb73ed179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7a7a044]
wallpaper-tray(main+0x344)[0x804d344]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7290ebc]
wallpaper-tray[0x804bb81]

```

---

### Post by yabbadabbadont on 2007-09-23
Known bug: [https://bugs.launchpad.net/ubuntu/+source/wallpaper-tray/+bug/95917](https://bugs.launchpad.net/ubuntu/+source/wallpaper-tray/+bug/95917)

Add your details to that bug and see if you can get its status changed to confirmed.  Odds are that it'll be ignored as Gutsy is due to be released next month.

---

