---
title: "Firefox keeps on freezing and crashing"
date: 2007-09-29
forum: General Help
---

### Post by elliotjreed on 2007-09-29
I am using Ubuntu Feisty with great results so far. However, the one thing that is really annoying me is Firefox.

Each time I use Firefox it crashes or freezes within about 10 minutes. :confused:

I have tried disabling extensions, uninstalling them, etc. but with no results.

I have run Firefox in terminal and it spits out the following:-

```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault (core dumped)
```

I have no idea what to do, I am also using Opera, which doesn't crash or freeze, but makes websites look ugly. :(

Please help me make Firefox work again!

Thanks

---

### Post by Happy_Man on 2007-09-29
Enter the command ```
sudo apt-get remove --purge firefox
``` and then ```
sudo apt-get install firefox
``` See if that works.

---

### Post by elliotjreed on 2007-09-29
Will that remove all of my settings, addons, passwords, etc... ?

Thanks

---

### Post by Happy_Man on 2007-09-29
Well..... yeah, I think so. So you should back up your profile folder (~/.mozilla/firefox) just to be safe, I guess.

---

### Post by Sabrage on 2007-09-29
Have you tried epiphany? I had the same problems with Firefox and Opera, but no problems with Epiphany.

edit: Only one problem: the totem-mozilla plugin didn't work and had to be removed.

---

### Post by LPomfrey on 2007-09-29
Have you tried running it in safe mode (with all add-ons and plug ins disabled)?

If it works when you do that I'd disable all of your add-ons and gradually add them back one at a time to see if it's one of them that's causing the problem.




And running "sudo apt-get remove --purge firefox" shouldn't remove the configuration files in your profile folder only the ones in /etc.

---

### Post by elliotjreed on 2007-10-02
Tried installing, then uninstalling!

But unfortunatly, no luck...

I am now getting this error message in the terminal:

```
elliot@Dell:~$ firefox
RMD :: mismatch remembered
*** glibc detected *** /usr/lib/firefox/firefox-bin: double free or corruption (!prev): 0x0a6f52f0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76c07cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76c3e30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb784ed11]
/usr/lib/libstdc++.so.6(_ZdaPv+0x1d)[0xb784ed6d]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb5f0b0c4]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb5f0b178]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb5f1a8fd]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb5f08f91]
/usr/lib/firefox/components/libgklayout.so[0xb5bc662e]
/usr/lib/firefox/components/libgklayout.so[0xb5bc4b45]
/usr/lib/firefox/components/libgklayout.so[0xb591005c]
/usr/lib/firefox/components/libgklayout.so[0xb5954bf8]
/usr/lib/firefox/components/libgklayout.so[0xb590bb17]
/usr/lib/firefox/components/libgklayout.so[0xb5a22f85]
/usr/lib/firefox/components/libgklayout.so[0xb5a415a4]
/usr/lib/firefox/components/libgklayout.so[0xb5a52759]
/usr/lib/firefox/components/libgklayout.so[0xb5917203]
/usr/lib/firefox/components/libgklayout.so[0xb590bae5]
/usr/lib/firefox/components/libgklayout.so[0xb5a22f85]
/usr/lib/firefox/components/libgklayout.so[0xb5917203]
/usr/lib/firefox/components/libgklayout.so[0xb590bae5]
/usr/lib/firefox/components/libgklayout.so[0xb5a22f85]
/usr/lib/firefox/components/libgklayout.so[0xb5917203]
/usr/lib/firefox/components/libgklayout.so[0xb590bae5]
/usr/lib/firefox/components/libgklayout.so[0xb59647ef]
/usr/lib/firefox/components/libgklayout.so[0xb58daf17]
/usr/lib/firefox/components/libgklayout.so[0xb58eb421]
/usr/lib/firefox/components/libgklayout.so[0xb58d8be6]
/usr/lib/firefox/components/libdocshell.so[0xb56997af]
/usr/lib/firefox/components/libnsappshell.so[0xb566a714]
/usr/lib/firefox/components/libnsappshell.so[0xb566f6b6]
/usr/lib/firefox/components/libnsappshell.so[0xb5660564]
/usr/lib/firefox/components/libgklayout.so[0xb5bede2b]
/usr/lib/firefox/components/libgklayout.so[0xb5bee248]
/usr/lib/firefox/libxpcom_core.so(PL_HandleEvent+0x27)[0xb7e24427]
/usr/lib/firefox/libxpcom_core.so(PL_ProcessPendingEvents+0x5b)[0xb7e2473b]
/usr/lib/firefox/libxpcom_core.so[0xb7e267c8]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb5f0e6c5]
/usr/lib/libglib-2.0.so.0[0xb752540d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb74fbdf2]
/usr/lib/libglib-2.0.so.0[0xb74fedcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb74ff179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7b3b044]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb5f0eb22]
/usr/lib/firefox/components/libtoolkitcomps.so[0xb5df8d92]
/usr/lib/firefox/firefox-bin[0x804ea79]
/usr/lib/firefox/firefox-bin[0x804ab8f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb766eebc]
/usr/lib/firefox/firefox-bin[0x804aac1]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 08:06 2342932    /usr/lib/firefox/firefox-bin
0805b000-0805d000 rw-p 00012000 08:06 2342932    /usr/lib/firefox/firefox-bin
0805d000-0ab06000 rw-p 0805d000 00:00 0          [heap]
aab5b000-aab5c000 ---p aab5b000 00:00 0 
aab5c000-ab35c000 rw-p aab5c000 00:00 0 
acb57000-acd30000 r--p 00000000 08:06 2707761    /usr/share/icons/hicolor/icon-theme.cache
acd30000-ae524000 r--p 00000000 08:06 2949398    /usr/share/icons/crystalsvg/icon-theme.cache
ae524000-aebcd000 r--p 00000000 08:06 2707717    /usr/share/icons/gnome/icon-theme.cache
aebcd000-aee24000 r--p 00000000 08:06 2707578    /usr/share/icons/Tango/icon-theme.cache
aee24000-aeec5000 r--p 00000000 08:06 2706614    /usr/share/icons/Tangerine/icon-theme.cache
aeec5000-af02b000 r--p 00000000 08:06 2705068    /usr/share/icons/Human/icon-theme.cache
af02b000-af02c000 ---p af02b000 00:00 0 
af02c000-af82c000 rw-p af02c000 00:00 0 
af8d9000-af910000 r--p 00000000 08:06 7536736    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf
af910000-af98d000 r--p 00000000 08:06 2590640    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
af98d000-afa0a000 r--p 00000000 08:06 2590640    /usr/share/fonKilled
```

I mean, what?

---

### Post by Happy_Man on 2007-10-04
Wow.... that is something I have never seen before. You sure this is the version in the repos? Because, that doesn't look like an error, that looks more like an activity dump. Just saying....

---

### Post by elliotjreed on 2007-10-05
Yep! It definitly the one that was already installed!

I did uninstall and then reinstall using the apt-get though, if that makes any difference!

---

