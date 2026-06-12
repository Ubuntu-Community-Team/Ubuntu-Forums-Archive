---
title: "Pidgin-libnotify has stopped working."
date: 2008-04-30
forum: General Help
---

### Post by merlinfmct87 on 2008-04-30
Hello, all

I've been using Pidgin-libnotify for a while now, and it's been very reliable. However, recently it's stopped working and I'm not sure why.

The only error message I've gotten is:

```
merlin@Familiar:~$ pidgin
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
libnotify-Message: Unable to get session bus: Failed to execute dbus-launch to autolaunch D-Bus session

```The first error I get when Pidgin starts up. The second is when I try to enable libnotify in the plugin list.

I've tried re-installing dbus, libnotify, pidgin-libnotify, I've even tried messing around with the /etc/group file, making sure my user was included in the messagebus group. Google and the ubuntu forum search have turned up nothing.

Any help would be appreciated. :)

All best,

Adam

---

### Post by Dr Small on 2008-04-30
Does it do the same thing if you run it with sudo?

---

### Post by merlinfmct87 on 2008-05-01
Interestingly enough, no. I'm able to load up the plugin and configure it.

Output from running it on the command line:

```
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files

```

That's after enabling libnotify. I'm waiting on some happy soul in my buddy list to message me or sign on/off so I can be sure the notifications are running properly. Pidgin started from scratch, however -- I'm assuming it's reading /root, rather than /home/merlin.

Well, that's some progress, at least. What do I do now?

Merlin

---

### Post by merlinfmct87 on 2008-05-04
Friendly self-bump.

Adam

---

### Post by sweetsinse on 2008-05-07
libnotify-Message: Unable to get session bus: Failed to execute dbus-launch to autolaunch D-Bus session

i get that same error under Xubuntu hardy.

the interesting thing is...  if i close pidgin, delete the .purple folder in my home directory, then restart fresh, the plugin works perfectly.  but as soon as i logout/shutdown/restart then log back in the plugin stops working again..??

it always works after i delete the .purple folder, but never when i reinstate a backed up .purpleBAK folder.

---

### Post by sweetsinse on 2008-05-09
after searching for a really, really long time i found a fix...  not sure the actual cause of the problem but this will work for me.

launch pidgin like this:

/usr/bin/dbus-launch /usr/bin/pidgin

-or-

dbus-launch pidgin


i renamed pidgin to pidgin.real and made a script that does it for me, similar to compiz/compiz.real

peace

---

### Post by KlausPaiva on 2008-06-30
> **sweetsinse said:**
> after searching for a really, really long time i found a fix...  not sure the actual cause of the problem but this will work for me.

launch pidgin like this:

/usr/bin/dbus-launch /usr/bin/pidgin

-or-

dbus-launch pidgin


i renamed pidgin to pidgin.real and made a script that does it for me, similar to compiz/compiz.real

peace

Great! Thanks!

---

### Post by Zetheroo on 2008-10-13
I am having a similar issue ... except that I don't have Pidgin-libnotify installed.

Here is my output from the Terminal:

> zeth@zeth-ubuntu:~$ pidgin
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
*** glibc detected *** pidgin: double free or corruption (fasttop): 0x0830f6c0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75aea85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75b24f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb770fc61]
/usr/lib/libpurple.so.0[0xb782972f]
/usr/lib/libpurple.so.0(purple_proxy_get_setup+0x92)[0xb782d22c]
/usr/lib/libpurple.so.0(purple_proxy_connect+0x10f)[0xb782d57a]
/usr/lib/libpurple.so.0[0xb7842714]
/usr/lib/libpurple.so.0[0xb784194e]
/usr/lib/libpurple.so.0[0xb7851bf7]
pidgin[0x80abca3]
/usr/lib/libglib-2.0.so.0[0xb773c0ed]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x176)[0xb7707dd6]
/usr/lib/libglib-2.0.so.0[0xb770b193]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb770b577]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7bc9264]
pidgin(main+0xbbc)[0x80c70d5]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7559450]
pidgin[0x806c821]
======= Memory map: ========
08048000-08115000 r-xp 00000000 08:02 3025217    /usr/bin/pidgin
08115000-08118000 rw-p 000cc000 08:02 3025217    /usr/bin/pidgin
08118000-08695000 rw-p 08118000 00:00 0          [heap]
b4100000-b4121000 rw-p b4100000 00:00 0 
b4121000-b4200000 ---p b4121000 00:00 0 
b424d000-b4351000 rw-p b424d000 00:00 0 
b4351000-b43d8000 r--p 00000000 08:02 3139152    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b43d8000-b43ef000 r--s 00000000 08:02 1261887    /var/lib/aspell/en_GB-ise-wo_accents-only.rws
b43ef000-b4406000 r--s 00000000 08:02 1261891    /var/lib/aspell/en_US-wo_accents-only.rws
b4406000-b468e000 r--s 00000000 08:02 1261879    /var/lib/aspell/en-common.rws
b468e000-b4792000 rw-p b468e000 00:00 0 
b4792000-b4794000 r-xp 00000000 08:02 3073925    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4794000-b4795000 rw-p 00001000 08:02 3073925    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4795000-b4826000 r--p 00000000 08:02 3139153    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4826000-b482c000 r--s 00000000 08:02 1261632    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b482c000-b482f000 r--s 00000000 08:02 1261642    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b482f000-b4830000 r--s 00000000 08:02 1261634    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b4830000-b4831000 r--s 00000000 08:02 1261627    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4831000-b4834000 r--s 00000000 08:02 1261633    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b4834000-b483b000 r--s 00000000 08:02 1262201    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b483b000-b483e000 r--s 00000000 08:02 1261639    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b483e000-b4846000 r--s 00000000 08:02 1261643    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4846000-b484e000 r--s 00000000 08:02 1261622    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b484e000-b485d000 r-xp 00000000 08:02 4153382    /lib/libbz2.so.1.0.4
b485d000-b485e000 rw-p 0000f000 08:02 4153382    /lib/libbz2.so.1.0.4
b485e000-b48bd000 r-xp 00000000 08:02 3023608    /usr/lib/libgio-2.0.so.0.0.0
b48bd000-b48bf000 rw-p 0005e000 08:02 3023608    /usr/lib/libgio-2.0.so.0.0.0
b48bf000-b48f1000 r-xp 00000000 08:02 3024324    /usr/lib/libcroco-0.6.so.3.0.1
b48f1000-b48f4000 rw-p 00031000 08:02 3024324    /usr/lib/libcroco-0.6.so.3.0.1
b48f4000-b4924000 r-xp 00000000 08:02 1671254    /usr/lib/libgsf-1.so.114.0.7
b4924000-b4927000 rw-p 0002f000 08:02 1671254    /usr/lib/libgsf-1.so.114.0.7
b4927000-b4928000 rw-p b4927000 00:00 0 
b4928000-b4958000 r-xp 00000000 08:02 1671577    /usr/lib/librsvg-2.so.2.22.2
b4958000-b4959000 rw-p 00030000 08:02 1671577    /usr/lib/librsvg-2.so.2.22.2
b4959000-b495c000 r--s 00000000 08:02 1261640    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b495c000-b4963000 r--s 00000000 08:02 1261637    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4963000-b4969000 r--s 00000000 08:02 1261621    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4969000-b496b000 r--s 00000000 08:02 1262001    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b496b000-b496c000 r-xp 00000000 08:02 3040027    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b496c000-b496d000 rw-p 00000000 08:02 3040027    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b496d000-b496e000 r--p 00000000 08:02 3073983    /usr/share/locale-langpack/en_AU/LC_MESSAGES/launchpad-integration.mo
b496e000-b4982000 r--p 00000000 08:02 26265      /home/zeth/.local/share/icons/hicolor/icon-theme.cache
b4982000-b4d2e000 r--p 00000000 08:02 3221814    /usr/share/icons/hicolor/icon-theme.cache
b4d2e000-b4d8e000 rw-s 00000000 00:09 9043985    /SYSV00000000 (deleted)
b4d8e000-b4d95000 r-xp 00000000 08:02 3039984    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b4d95000-b4d96000 rw-p 00007000 08:02 3039984    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b4d96000-b4dda000 r-xp 00000000 08:02 335876     /usr/lib/nss/libnssckbi.so
b4dda000-b4de5000 rw-p 00044000 08:02 335876     /usr/lib/nss/libnssckbi.so
b4de5000-b4e1f000 r-xp 00000000 08:02 335873     /usr/lib/nss/libfreebl3.so
b4e1f000-b4e20000 rw-p 0003a000 08:02 335873     /usr/lib/nss/libfreebl3.so
b4e20000-b4e50000 r-xp 00000000 08:02 335874     /usr/lib/nss/libsoftokn3.so
b4e50000-b4e51000 rw-p 00030000 08:02 335874     /usr/lib/nss/libsoftokn3.so
b4e51000-b4e52000 ---p b4e51000 00:00 0 
b4e52000-b5652000 rw-p b4e52000 00:00 0 
b5652000-b5669000 r-xp 00000000 08:02 3491522    /usr/lib/purple-2/libmyspace.so
b5669000-b566b000 rw-p 00016000 08:02 3491522    /usr/lib/purple-2/libmyspace.so
b566b000-b567f000 r-xp 00000000 08:02 3024436    /usr/lib/libgadu.so.3.5
b567f000-b5680000 rw-p 00013000 08:02 3024436    /usr/lib/libgadu.so.3.5
b5680000-b5684000 r-xp 00000000 08:02 3040019    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5684000-b5685000 rw-p 00003000 08:02 3040019    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5685000-b5687000 r-xp 00000000 08:02 3491513    /usr/lib/purple-2/psychic.so
b5687000-b5688000 rw-p 00001000 08:02 3491513    /usr/lib/purple-2/psychic.so
b5688000-b5691000 r-xp 00000000 08:02 3491510    /usr/lib/purple-2/log_reader.so
b5691000-b5692000 rw-p 00008000 08:02 3491510    /usr/lib/purple-2/log_reader.so
b5692000-b569e000 r-xp 00000000 08:02 3491517    /usr/lib/purple-2/libgg.so
b569e000-b569f000 rw-p 0000b000 08:02 3491517    /usr/lib/purple-2/libgg.so
b569f000-b56cc000 r-xp 00000000 08:02 4153424    /lib/libncurses.so.5.6
b56cc000-b56cf000 rw-p 0002c000 08:02 4153424    /lib/libncurses.so.5.6
b56cf000-b56fb000 r-xp 00000000 08:02 4153464    /lib/libreadline.so.5.2
b56fb000-b56ff000 rw-p 0002c000 08:02 4153464    /lib/libreadline.so.5.2
b56ff000-b5700000 rw-p b56ff000 00:00 0 
b5700000-b570a000 r-xp 00000000 08:02 1671708    /usr/lib/libzephyr.so.3.0.0
b570a000-b570b000 rw-p 00009000 08:02 1671708    /usr/lib/libzephyr.so.3.0.0
b570b000-b570e000 rw-p b570b000 00:00 0 
b570e000-b571e000 r-xp 00000000 08:02 3491516    /usr/lib/purple-2/libbonjour.so
b571e000-b571f000 rw-p 00010000 08:02 3491516    /usr/lib/purple-2/libbonjour.so
b571f000-b5720000 rw-p b571f000 00:00 0 
b5720000-b5721000 ---p b5720000 00:00 0 
b5721000-b5f21000 rw-p b5721000 00:00 0 
b5f21000-b5ff3000 r-xp 00000000 08:02 1671617    /usr/lib/libtk8.4.so.0
b5ff3000-b5ffe000 rw-p 000d2000 08:02 1671617    /usr/lib/libtk8.4.so.0
b5ffe000-b5fff000 rw-p b5ffe000 00:00 0 
b5fff000-b60a8000 r-xp 00000000 08:02 1671616    /usr/lib/libtcl8.4.so.0
b60a8000-b60b2000 rw-p 000a8000 08:02 1671616    /usr/lib/libtcl8.4.so.0
b60b2000-b60b3000 rw-p b60b2000 00:00 0 
b60b5000-b60b7000 r-xp 00000000 08:02 3491506    /usr/lib/purple-2/autoaccept.so
b60b7000-b60b8000 rw-p 00001000 08:02 3491506    /usr/lib/purple-2/autoaccept.so
b60b8000-b60c4000 r-xp 00000000 08:02 3491531    /usr/lib/purple-2/libzephyr.so
b60c4000-b60c5000 rw-p 0000c000 08:02 3491531    /usr/lib/purple-2/libzephyr.so
b60c5000-b61e0000 r-xp 00000000 08:02 1671516    /usr/lib/libperl.so.5.8.8
b61e0000-b61e5000 rw-p 0011a000 08:02 1671516    /usr/lib/libperl.so.5.8.8
b61e5000-b61e7000 rw-p b61e5000 00:00 0 
b61e9000-b61f8000 r-xp 00000000 08:02 3491505    /usr/lib/purple-2/tcl.so
b61f8000-b61f9000 rw-p 0000f000 08:02 3491505    /usr/lib/purple-2/tcl.so
b61f9000-b6204000 r-xp 00000000 08:02 3491501    /usr/lib/purple-2/perl.so
b6204000-b6205000 rw-p 0000b000 08:02 3491501    /usr/lib/purple-2/perl.so
b6205000-b6240000 r-xp 00000000 08:02 3491530    /usr/lib/purple-2/libyahoo.so
b6240000-b6242000 rw-p 0003b000 08:02 3491530    /usr/lib/purple-2/libyahoo.so
b6242000-b6254000 r-xp 00000000 08:02 3491518    /usr/lib/purple-2/libirc.so
b6254000-b6255000 rw-p 00012000 08:02 3491518    /usr/lib/purple-2/libirc.so
b6255000-b6260000 r-xp 00000000 08:02 3491529    /usr/lib/purple-2/libsimple.so
b6260000-b6261000 rw-p 0000a000 08:02 3491529    /usr/lib/purple-2/libsimple.so
b6261000-b6271000 rw-p b6261000 00:00 0 
b6271Aborted

---

