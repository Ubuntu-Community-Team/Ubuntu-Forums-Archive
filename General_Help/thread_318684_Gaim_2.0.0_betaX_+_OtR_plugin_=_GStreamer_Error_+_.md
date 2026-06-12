---
title: "Gaim 2.0.0 betaX + OtR plugin = GStreamer Error + Connection Error?"
date: 2006-12-14
forum: General Help
---

### Post by digitalsynthesis on 2006-12-14
So I've searched my eyeballs off and cannot find a solution or even a cause to this problem.  It was listed in a few places as an isolated bug, but apparently I'm experiencing this "isolated bug" as well now.  I *just* switched to Kubuntu 6.10 Edgy Eft, and on a clean install I added GAIM_OTR and am now completely unable to connect to any accounts in GAIM.  

What's crazy is that I completely blew away and reinstalled Edgy just to see if I did something wrong and this happened again, on a pristine install.

The error is indicated by a GStreamer Failed to Initialize dialogue, and then the accounts fail by saying "unable to send request to resolver process".  When I remove the OTR plugin, everything works perfectly, no problems.

I downloaded the brand new OtR code, applied the GAIM 2.0 patch, changed the include to gaimstock.h instead of gtkstock.h as posted in another thread on this forum, and recompiled/installed the OtR code from source, and still get the same problem.  Likewise with the stock packages.

I have gaim -d debug traces if anybody wants them.  This is driving me nuts, however and its really given me a bad taste for Kubuntu if right off the bat the stock packages do not work correctly.  However, I'm willing to stick this problem out as I really do not want to consider running alternative distros.  If anybody is willing to help get to the bottom of this apparently rare but definitely present bug, I would be greatly appreciative.

---

### Post by digitalsynthesis on 2006-12-14
**Debug output with OTR:**

[Thu Dec 14 14:24:21]$ gaim -d
dbus: okkk
plugins: probing /usr/lib/gaim/musicmessaging.so
plugins: probing /usr/lib/gaim/dbus-example.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaimrc.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: /usr/lib/gaim/gevolution.so is not loadable: libedata-book-1.2.so.2: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/gaim-otr.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: probing /usr/lib/gaim/libsametime.so
plugins: /usr/lib/gaim/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
plugins: probing /usr/lib/gaim/libsimple.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is not loadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/perl.so
plugins: probing /usr/lib/gaim/psychic.so
plugins: probing /usr/lib/gaim/relnot.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: /usr/lib/gaim/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/timestamp_format.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/libbonjour.so
plugins: probing /usr/lib/gaim/gnthistory.so
plugins: probing /usr/lib/gaim/gntlastlog.so
plugins: /usr/lib/gaim/gntlastlog.so is not loadable: undefined symbol: cur_term
plugins: probing /usr/lib/gaim/log_reader.so
plugins: probing /usr/lib/gaim/libqq.so
util: Reading file accounts.xml from directory /home/<my user name>/.gaim
util: Reading file status.xml from directory /home/<my user name>/.gaim
stun: using server
stun: using server
sound: Initializing sound output drivers.
*** glibc detected *** gaim: free(): invalid pointer: 0x0811c380 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb735d8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb735da44]
/usr/lib/libotr.so.2[0xb6d0228a]
/usr/lib/libgcrypt.so.11(gcry_free+0x28)[0xb6f9e58b]
/usr/lib/libgcrypt.so.11(gcry_cipher_close+0x84)[0xb6fa3ae8]
/usr/lib/libgnutls.so.13[0xb70dc37d]
/usr/lib/libgnutls.so.13(_gnutls_cipher_deinit+0x21)[0xb70bc541]
/usr/lib/libgnutls.so.13(gnutls_deinit+0xff)[0xb70cfc6f]
/usr/lib/libldap_r.so.2(gnutls_SSL_free+0x2c)[0xb71a351c]
/usr/lib/libldap_r.so.2[0xb71a113f]
/usr/lib/liblber.so.2(ber_sockbuf_remove_io+0x80)[0xb7172e90]
/usr/lib/liblber.so.2(ber_int_sb_destroy+0x4a)[0xb7172f4a]
/usr/lib/liblber.so.2(ber_sockbuf_free+0x34)[0xb7172ff4]
/usr/lib/libldap_r.so.2(ldap_ld_free+0x1b1)[0xb718b5a1]
/lib/libnss_ldap.so.2[0xb71ae170]
/lib/libnss_ldap.so.2[0xb71b1eb9]
/lib/tls/i686/cmov/libc.so.6(fork+0x1de)[0xb738607e]
/lib/tls/i686/cmov/libpthread.so.0(fork+0x14)[0xb76542d4]
/usr/lib/libgstreamer-0.10.so.0[0xb7f210fb]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x1f4)[0xb75ed814]
/usr/lib/libgstreamer-0.10.so.0(gst_init_check+0xa1)[0xb7f200b1]
gaim[0x80c92ee]
/usr/lib/libgaim.so.0(gaim_sound_set_ui_ops+0x40)[0xb77454c0]
gaim[0x80ab621]
/usr/lib/libgaim.so.0(gaim_core_init+0x152)[0xb771e582]
gaim(main+0x630)[0x80abce0]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb730c8cc]
gaim(gtk_widget_grab_focus+0x35)[0x8067081]
======= Memory map: ========
08048000-080e5000 r-xp 00000000 03:01 9012811    /usr/bin/gaim
080e5000-080e8000 rw-p 0009d000 03:01 9012811    /usr/bin/gaim
080e8000-08181000 rw-p 080e8000 00:00 0          [heap]
b6800000-b6821000 rw-p b6800000 00:00 0
b6821000-b6900000 ---p b6821000 00:00 0
b69e6000-b6a0f000 r-xp 00000000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a0f000-b6a10000 rw-p 00028000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a10000-b6a1e000 r-xp 00000000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1e000-b6a1f000 rw-p 0000e000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1f000-b6a29000 r-xp 00000000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a29000-b6a2a000 rw-p 00009000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a2a000-b6a36000 r-xp 00000000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a36000-b6a37000 rw-p 0000b000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a3c000-b6a42000 r-xp 00000000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a42000-b6a43000 rw-p 00006000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a43000-b6a45000 r-xp 00000000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a45000-b6a46000 rw-p 00001000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a46000-b6a4d000 r-xp 00000000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4d000-b6a4e000 rw-p 00006000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4e000-b6a50000 r-xp 00000000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a50000-b6a51000 rw-p 00002000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a51000-b6a53000 r-xp 00000000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a53000-b6a54000 rw-p 00001000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a54000-b6a59000 r-xp 00000000 03:01 9225789    /usr/lib/gaim/ticker.so
b6a59000-b6a5a000 rw-p 00004000 03:01 9225789    /usr/lib/gaim/ticker.so
b6a5a000-b6a5b000 r-xp 00000000 03:01 9225779    /usr/lib/gaim/ssl.so
b6a5b000-b6a5c000 rw-p 00000000 03:01 9225779    /usr/lib/gaim/ssl.so
b6a5c000-b6a5d000 r-xp 00000000 03:01 9225768    /usr/lib/gaim/ssl-nss.so
b6a5d000-b6a5e000 rw-p 00000000 03:01 9225768    /usr/lib/gaim/ssl-nss.so
b6a5e000-b6a60000 r-xp 00000000 03:01 9225762    /usr/lib/gaim/statenotify.so
b6a60000-b6a61000 rw-p 00001000 03:01 9225762    /usr/lib/gaim/statenotify.so
b6a61000-b6b71000 r-xp 00000000 03:01 9014802    /usr/lib/libperl.so.5.8.8
b6b71000-b6b76000 rw-p 00110000 03:01 9014802    /usr/lib/libperl.so.5.8.8
b6b76000-b6b78000 rw-p b6b76000 00:00 0
b6b78000-b6b86000 r-xp 00000000 03:01 9225773    /usr/lib/gaim/spellchk.so
b6b86000-b6b87000 rw-p 0000e000 03:01 9225773    /usr/lib/gaim/spellchk.so
b6b87000-b6b90000 r-xp 00000000 03:01 9225786    /usr/lib/gaim/perl.so
b6b90000-b6b91000 rw-p 00008000 03:01 9225786    /usr/lib/gaim/perl.so
b6b91000-b6bc4000 r-xp 00000000 03:01 9225763    /usr/lib/gaim/libyahoo.so
b6bc4000-b6bc6000 rw-p 00033000 03:01 9225763    /usr/lib/gaim/libyahoo.so
b6bc6000-b6bcf000 r-xp 00000000 03:01 9225759    /usr/lib/gaim/libsimple.so
b6bcf000-b6bd0000 rw-p 00008000 03:01 9225759    /usr/lib/gaim/libsimple.so
b6bd0000-b6be0000 rw-p b6bd0000 00:00 0
b6be0000-b6c07000 r-xp 00000000 03:01 9012744    /usr/lib/libmeanwhile.so.1.0.2
b6c07000-b6c08000 rw-p 00026000 03:01 9012744    /usr/lib/libmeanwhile.so.1.0.2
b6c08000-b6c1c000 r-xp 00000000 03:01 9225774    /usr/lib/gaim/libsametime.so
b6c1c000-b6c1d000 rw-p 00013000 03:01 9225774    /usr/lib/gaim/libsametime.so
b6c1d000-b6c1e000 rw-p b6c1d000 00:00 0
b6c1e000-b6c58000 r-xp 00000000 03:01 9225782    /usr/lib/gaim/liboscar.so
b6c58000-b6c5a000 rw-p 00039000 03:01 9225782    /usr/lib/gaim/liboscar.so
b6c5a000-b6c72000 r-xp 00000000 03:01 9225753    /usr/lib/gaim/libnovell.so
b6c72000-b6c73000 rw-p 00018000 03:01 9225753    /usr/lib/gaim/libnovell.so
b6c73000-b6c9b000 r-xp 00000000 03:01 9225755    /usr/lib/gaim/libmsn.so
b6c9b000-b6c9c000 rw-p 00028000 03:01 9225755    /usr/lib/gaim/libmsn.so
b6c9c000-b6c9f000 rw-p b6c9c000 00:00 0
b6c9f000-b6cc2000 r-xp 00000000 03:01 9225769    /usr/lib/gaim/libjabber.so
b6cc2000-b6cc3000 rw-p 00023000 03:01 9225769    /usr/lib/gaim/libjabber.so
b6cc3000-b6cc6000 rw-p b6cc3000 00:00 0
b6cc6000-b6cd7000 r-xp 00000000 03:01 9225754    /usr/lib/gaim/libirc.so
b6cd7000-b6cd8000 rw-p 00010000 03:01 9225754 *** glibc detected *** gaim: free(): invalid pointer: 0x0811c380 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb735d8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb735da44]
/usr/lib/libotr.so.2[0xb6d0228a]
/usr/lib/libgcrypt.so.11(gcry_free+0x28)[0xb6f9e58b]
/usr/lib/libgcrypt.so.11(gcry_cipher_close+0x84)[0xb6fa3ae8]
/usr/lib/libgnutls.so.13[0xb70dc37d]
/usr/lib/libgnutls.so.13(_gnutls_cipher_deinit+0x21)[0xb70bc541]
/usr/lib/libgnutls.so.13(gnutls_deinit+0xff)[0xb70cfc6f]
/usr/lib/libldap_r.so.2(gnutls_SSL_free+0x2c)[0xb71a351c]
/usr/lib/libldap_r.so.2[0xb71a113f]
/usr/lib/liblber.so.2(ber_sockbuf_remove_io+0x80)[0xb7172e90]
/usr/lib/liblber.so.2(ber_int_sb_destroy+0x4a)[0xb7172f4a]
/usr/lib/liblber.so.2(ber_sockbuf_free+0x34)[0xb7172ff4]
/usr/lib/libldap_r.so.2(ldap_ld_free+0x1b1)[0xb718b5a1]
/lib/libnss_ldap.so.2[0xb71ae170]
/lib/libnss_ldap.so.2[0xb71b1eb9]
/lib/tls/i686/cmov/libc.so.6(fork+0x1de)[0xb738607e]
/lib/tls/i686/cmov/libc.so.6(_IO_proc_open+0x9b)[0xb734ec6b]
/lib/tls/i686/cmov/libc.so.6(_IO_popen+0x6a)[0xb734eeca]
/usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so(_Z10runCommandRK7QString+0x49)[0xb69d8739]
/usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so(initKdeSettings+0x101)[0xb69d9bcb]
/usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so(createQApp+0x5dc)[0xb69da752]
/usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so(theme_init+0x1b)[0xb69cdc79]
/usr/lib/libgtk-x11-2.0.so.0[0xb7ccab06]
/usr/lib/libgobject-2.0.so.0(g_type_module_use+0x88)[0xb768eb18]
/usr/lib/libgtk-x11-2.0.so.0(gtk_theme_engine_get+0x49)[0xb7cca939]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4c7b0]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4ef33]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4fa7a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4feb2]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4fc4f]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4feb2]
/usr/lib/libgtk-x11-2.0.so.0(gtk_rc_reparse_all_for_settings+0xd4)[0xb7c503d4]
/usr/lib/libgtk-x11-2.0.so.0(gtk_settings_get_for_screen+0xe5)[0xb7c69cc5]
/usr/lib/libgtk-x11-2.0.so.0(gtk_settings_get_default+0x25)[0xb7c69d85]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c82c3c]
/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x4ca)[0xb768d89a]
/usr/lib/libgobject-2.0.so.0[0xb7674952]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x2cb)[0xb7672bdb]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb767373f]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb76738f0]
/usr/lib/libgtk-x11-2.0.so.0(gtk_style_new+0x27)[0xb7c7b097]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_get_default_style+0x2d)[0xb7d1c20d]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d1c2ae]
/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x2fe)[0xb768d6ce]
/usr/lib/libgobject-2.0.so.0[0xb7674952]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x2cb)[0xb7672bdb]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb767373f]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb76738f0]
/usr/lib/libgtk-x11-2.0.so.0(gtk_image_new_from_stock+0x2c)[0xb7be33ec]
gaim[0x80af2d5]
/usr/lib/libgaim.so.0(gaim_notify_message+0x71)[0xb772b1f1]
gaim[0x80c9384]
/usr/lib/libgaim.so.0(gaim_sound_set_ui_ops+0x40)[0xb77454c0]
gaim[0x80ab621]
/usr/lib/libgaim.so.0(gaim_core_init+0x152)[0xb771e582]
gaim(main+0x630)[0x80abce0]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb730c8cc]
gaim(gtk_widget_grab_focus+0x35)[0x8067081]
======= Memory map: ========
08048000-080e5000 r-xp 00000000 03:01 9012811    /usr/bin/gaim
080e5000-080e8000 rw-p 0009d000 03:01 9012811    /usr/bin/gaim
080e8000-08181000 rw-p 080e8000 00:00 0          [heap]
b6000000-b6021000 rw-p b6000000 00:00 0
b6021000-b6100000 ---p b6021000 00:00 0
b6144000-b6155000 r-xp 00000000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6155000-b6156000 rw-p 00010000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6156000-b6174000 r-xp 00000000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6174000-b6175000 rw-p 0001d000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6175000-b61bf000 r-xp 00000000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61bf000-b61c3000 rw-p 00049000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61c3000-b61d8000 r-xp 00000000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d8000-b61d9000 rw-p 00014000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d9000-b696e000 r-xp 00000000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b696e000-b69b5000 rw-p 00794000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b69b5000-b69b8000 rw-p b69b5000 00:00 0
b69c7000-b69e5000 r-xp 00000000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e5000-b69e6000 rw-p 0001e000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e6000-b6a0f000 r-xp 00000000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a0f000-b6a10000 rw-p 00028000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a10000-b6a1e000 r-xp 00000000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1e000-b6a1f000 rw-p 0000e000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1f000-b6a29000 r-xp 00000000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a29000-b6a2a000 rw-p 00009000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a2a000-b6a36000 r-xp 00000000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a36000-b6a37000 rw-p 0000b000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a3c000-b6a42000 r-xp 00000000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a42000-b6a43000 rw-p 00006000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a43000-b6a45000 r-xp 00000000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a45000-b6a46000 rw-p 00001000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a46000-b6a4d000 r-xp 00000000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4d000-b6a4e000 rw-p 00006000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4e000-b6a50000 r-xp 00000000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a50000-b6a51000 rw-p 00002000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a51000-b6a53000 r-xp 00000000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a53000-b6a54000 rw-p 00001000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a54000-b6a59000 r-xp 00000000 03:01 9225789    /usr/lib/gaim/ticker.so
b6a59000-b6a5a000 rw-p 00004000 03:01 9225789    /usr/lib/gaim/ticker.so
b6a5a000-b6a5b000 r-xp 00000000 03:01 9225779    /usr/lib/gaim/ssl.so
b6a5b000-b6a5c000 rw-p 00000000 03:01 9225779    /usr/lib/gaim/ssl.so
b6a5c000-b6a5d000 r-xp 00000000 03:01 9225768    /usr/lib/gaim/ssl-nss.so
b6a5d000-b6a5e000 rw-p 00000000 03:01 9225768    /usr/lib/gaim/ssl-nss.so
b6a5e000-b6a60000 r-xp 00000000 03:01 9225762    /usr/lib/gaim/statenotify.so
b6a60000-b6a61000 rw-p 00001000 03:01 9225762    /usr/lib/gaim/statenotify.so
b6a61000-b6b71000 r-xp 00000000 03:01 9014802    /usr/lib/libperl.so.5.8.8
b6b71000-b6b76000 rw-p 00110000 03:01 9014802    /u*** glibc detected *** gaim: free(): invalid pointer: 0x0811c380 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb735d8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb735da44]
/usr/lib/libotr.so.2[0xb6d0228a]
/usr/lib/libgcrypt.so.11(gcry_free+0x28)[0xb6f9e58b]
/usr/lib/libgcrypt.so.11(gcry_cipher_close+0x84)[0xb6fa3ae8]
/usr/lib/libgnutls.so.13[0xb70dc37d]
/usr/lib/libgnutls.so.13(_gnutls_cipher_deinit+0x21)[0xb70bc541]
/usr/lib/libgnutls.so.13(gnutls_deinit+0xff)[0xb70cfc6f]
/usr/lib/libldap_r.so.2(gnutls_SSL_free+0x2c)[0xb71a351c]
/usr/lib/libldap_r.so.2[0xb71a113f]
/usr/lib/liblber.so.2(ber_sockbuf_remove_io+0x80)[0xb7172e90]
/usr/lib/liblber.so.2(ber_int_sb_destroy+0x4a)[0xb7172f4a]
/usr/lib/liblber.so.2(ber_sockbuf_free+0x34)[0xb7172ff4]
/usr/lib/libldap_r.so.2(ldap_ld_free+0x1b1)[0xb718b5a1]
/lib/libnss_ldap.so.2[0xb71ae170]
/lib/libnss_ldap.so.2[0xb71b1eb9]
/lib/tls/i686/cmov/libc.so.6(fork+0x1de)[0xb738607e]
/lib/tls/i686/cmov/libc.so.6(_IO_proc_open+0x9b)[0xb734ec6b]
/lib/tls/i686/cmov/libc.so.6(_IO_popen+0x6a)[0xb734eeca]
/usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so(_Z10runCommandRK7QString+0x49)[0xb69d8739]
/usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so(initKdeSettings+0x21c)[0xb69d9ce6]
/usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so(createQApp+0x5dc)[0xb69da752]
/usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so(theme_init+0x1b)[0xb69cdc79]
/usr/lib/libgtk-x11-2.0.so.0[0xb7ccab06]
/usr/lib/libgobject-2.0.so.0(g_type_module_use+0x88)[0xb768eb18]
/usr/lib/libgtk-x11-2.0.so.0(gtk_theme_engine_get+0x49)[0xb7cca939]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4c7b0]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4ef33]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4fa7a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4feb2]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4fc4f]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c4feb2]
/usr/lib/libgtk-x11-2.0.so.0(gtk_rc_reparse_all_for_settings+0xd4)[0xb7c503d4]
/usr/lib/libgtk-x11-2.0.so.0(gtk_settings_get_for_screen+0xe5)[0xb7c69cc5]
/usr/lib/libgtk-x11-2.0.so.0(gtk_settings_get_default+0x25)[0xb7c69d85]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c82c3c]
/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x4ca)[0xb768d89a]
/usr/lib/libgobject-2.0.so.0[0xb7674952]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x2cb)[0xb7672bdb]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb767373f]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb76738f0]
/usr/lib/libgtk-x11-2.0.so.0(gtk_style_new+0x27)[0xb7c7b097]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_get_default_style+0x2d)[0xb7d1c20d]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d1c2ae]
/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x2fe)[0xb768d6ce]
/usr/lib/libgobject-2.0.so.0[0xb7674952]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x2cb)[0xb7672bdb]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb767373f]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb76738f0]
/usr/lib/libgtk-x11-2.0.so.0(gtk_image_new_from_stock+0x2c)[0xb7be33ec]
gaim[0x80af2d5]
/usr/lib/libgaim.so.0(gaim_notify_message+0x71)[0xb772b1f1]
gaim[0x80c9384]
/usr/lib/libgaim.so.0(gaim_sound_set_ui_ops+0x40)[0xb77454c0]
gaim[0x80ab621]
/usr/lib/libgaim.so.0(gaim_core_init+0x152)[0xb771e582]
gaim(main+0x630)[0x80abce0]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb730c8cc]
gaim(gtk_widget_grab_focus+0x35)[0x8067081]
======= Memory map: ========
08048000-080e5000 r-xp 00000000 03:01 9012811    /usr/bin/gaim
080e5000-080e8000 rw-p 0009d000 03:01 9012811    /usr/bin/gaim
080e8000-08181000 rw-p 080e8000 00:00 0          [heap]
b6000000-b6021000 rw-p b6000000 00:00 0
b6021000-b6100000 ---p b6021000 00:00 0
b6144000-b6155000 r-xp 00000000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6155000-b6156000 rw-p 00010000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6156000-b6174000 r-xp 00000000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6174000-b6175000 rw-p 0001d000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6175000-b61bf000 r-xp 00000000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61bf000-b61c3000 rw-p 00049000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61c3000-b61d8000 r-xp 00000000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d8000-b61d9000 rw-p 00014000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d9000-b696e000 r-xp 00000000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b696e000-b69b5000 rw-p 00794000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b69b5000-b69b8000 rw-p b69b5000 00:00 0
b69c7000-b69e5000 r-xp 00000000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e5000-b69e6000 rw-p 0001e000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e6000-b6a0f000 r-xp 00000000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a0f000-b6a10000 rw-p 00028000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a10000-b6a1e000 r-xp 00000000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1e000-b6a1f000 rw-p 0000e000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1f000-b6a29000 r-xp 00000000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a29000-b6a2a000 rw-p 00009000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a2a000-b6a36000 r-xp 00000000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a36000-b6a37000 rw-p 0000b000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a3c000-b6a42000 r-xp 00000000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a42000-b6a43000 rw-p 00006000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a43000-b6a45000 r-xp 00000000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a45000-b6a46000 rw-p 00001000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a46000-b6a4d000 r-xp 00000000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4d000-b6a4e000 rw-p 00006000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4e000-b6a50000 r-xp 00000000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a50000-b6a51000 rw-p 00002000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a51000-b6a53000 r-xp 00000000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a53000-b6a54000 rw-p 00001000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a54000-b6a59000 r-xp 00000000 03:01 9225789    /usr/lib/gaim/tickeX Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
util: Reading file blist.xml from directory /home/<my user name>/.gaim
prefs: Reading /home/<my user name>/.gaim/prefs.xml
prefs: Finished reading /home/<my user name>/.gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/ssl-gnutls.so
plugins: Loading saved plugin /usr/lib/gaim/gnthistory.so
plugins: Loading saved plugin /usr/lib/gaim/notify.so
plugins: Loading saved plugin /usr/lib/gaim/gaim-otr.so
plugins: Loading saved plugin /usr/lib/gaim/ssl.so
gtkblist: added visibility manager: 1
docklet: created
pounce: Error reading pounces: Failed to open file '/home/<my user name>/.gaim/pounces.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (KDE) with client ID 107a65726f000116612427700000049800050
Session Management: Using gaim as command
dbus: Need to register an object with the dbus subsystem.
g_log: file ../../libgaim/dbus-server.c: line 118 (gaim_dbus_pointer_to_id): should not be reached
account: Connecting to account < AIM Account 1 >
connection: Connecting. gc = 0x84b30e8
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: Adding handler for ffff/0003
oscar: Adding handler for ffff/0006
oscar: Adding handler for 0007/0003
oscar: Adding handler for 0007/0005
oscar: Adding handler for 0007/0007
oscar: Adding handler for 0018/0001
oscar: Adding handler for 0018/0007
oscar: Adding handler for 0017/0003
oscar: Adding handler for 0017/0007
oscar: Adding handler for 0017/000a
oscar: Adding handler for 0010/0001
oscar: Adding handler for 0010/0005
oscar: Adding handler for 0009/0001
oscar: Adding handler for 0009/0003
oscar: Adding handler for 0003/0001
oscar: Adding handler for 0003/0003
oscar: Adding handler for 0003/000b
oscar: Adding handler for 0003/000c
oscar: Adding handler for 000e/0001
oscar: Adding handler for 000e/0003
oscar: Adding handler for 000e/0004
oscar: Adding handler for 000e/0002
oscar: Adding handler for 000e/0006
oscar: Adding handler for 000d/0001
oscar: Adding handler for 000d/0009
oscar: Adding handler for 0013/0001
oscar: Adding handler for 0013/0003
oscar: Adding handler for 0013/0006
oscar: Adding handler for 0013/000e
oscar: Adding handler for 0013/0008
oscar: Adding handler for 0013/0015
oscar: Adding handler for 0013/0019
oscar: Adding handler for 0013/001b
oscar: Adding handler for 0013/001c
oscar: Adding handler for 0004/0005
oscar: Adding handler for 0004/0007
oscar: Adding handler for 0004/000a
oscar: Adding handler for 0004/000b
oscar: Adding handler for 0004/0001
oscar: Adding handler for 0004/0014
oscar: Adding handler for 0004/000c
oscar: Adding handler for 0015/00f0
oscar: Adding handler for 0015/00f1
oscar: Adding handler for 0015/00f3
oscar: Adding handler for 0015/00f2
oscar: Adding handler for 0002/0003
oscar: Adding handler for 0002/0006
oscar: Adding handler for 0002/0001
oscar: Adding handler for 0002/fffd
oscar: Adding handler for 0001/0001
oscar: Adding handler for 0001/000f
oscar: Adding handler for 0001/001f
oscar: Adding handler for 0001/0021
oscar: Adding handler for 0001/000a
oscar: Adding handler for 0001/0005
oscar: Adding handler for 0001/0013
oscar: Adding handler for 0001/0010
oscar: Adding handler for 0008/0002
oscar: Adding handler for 000a/0001
oscar: Adding handler for 000a/0003
oscar: oscar_login: gc = 0x84b30e8

---

### Post by digitalsynthesis on 2006-12-14
**Continued...**

dns: DNS query for 'login.oscar.aol.com' queued
account: Connecting to account < AIM Account 2 >
connection: Connecting. gc = 0x84b48f8
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: Adding handler for ffff/0003
oscar: Adding handler for ffff/0006
oscar: Adding handler for 0007/0003
oscar: Adding handler for 0007/0005
oscar: Adding handler for 0007/0007
oscar: Adding handler for 0018/0001
oscar: Adding handler for 0018/0007
oscar: Adding handler for 0017/0003
oscar: Adding handler for 0017/0007
oscar: Adding handler for 0017/000a
oscar: Adding handler for 0010/0001
oscar: Adding handler for 0010/0005
oscar: Adding handler for 0009/0001
oscar: Adding handler for 0009/0003
oscar: Adding handler for 0003/0001
oscar: Adding handler for 0003/0003
oscar: Adding handler for 0003/000b
oscar: Adding handler for 0003/000c
oscar: Adding handler for 000e/0001
oscar: Adding handler for 000e/0003
oscar: Adding handler for 000e/0004
oscar: Adding handler for 000e/0002
oscar: Adding handler for 000e/0006
oscar: Adding handler for 000d/0001
oscar: Adding handler for 000d/0009
oscar: Adding handler for 0013/0001
oscar: Adding handler for 0013/0003
oscar: Adding handler for 0013/0006
oscar: Adding handler for 0013/000e
oscar: Adding handler for 0013/0008
oscar: Adding handler for 0013/0015
oscar: Adding handler for 0013/0019
oscar: Adding handler for 0013/001b
oscar: Adding handler for 0013/001c
oscar: Adding handler for 0004/0005
oscar: Adding handler for 0004/0007
oscar: Adding handler for 0004/000a
oscar: Adding handler for 0004/000b
oscar: Adding handler for 0004/0001
oscar: Adding handler for 0004/0014
oscar: Adding handler for 0004/000c
oscar: Adding handler for 0015/00f0
oscar: Adding handler for 0015/00f1
oscar: Adding handler for 0015/00f3
oscar: Adding handler for 0015/00f2
oscar: Adding handler for 0002/0003
oscar: Adding handler for 0002/0006
oscar: Adding handler for 0002/0001
oscar: Adding handler for 0002/fffd
oscar: Adding handler for 0001/0001
oscar: Adding handler for 0001/000f
oscar: Adding handler for 0001/001f
oscar: Adding handler for 0001/0021
oscar: Adding handler for 0001/000a
oscar: Adding handler for 0001/0005
oscar: Adding handler for 0001/0013
oscar: Adding handler for 0001/0010
oscar: Adding handler for 0008/0002
oscar: Adding handler for 000a/0001
oscar: Adding handler for 000a/0003
oscar: oscar_login: gc = 0x84b48f8
dns: DNS query for 'login.oscar.aol.com' queued
account: Connecting to account < AIM Account 3 >
connection: Connecting. gc = 0x84b6b80
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: Adding handler for ffff/0003
oscar: Adding handler for ffff/0006
oscar: Adding handler for 0007/0003
oscar: Adding handler for 0007/0005
oscar: Adding handler for 0007/0007
oscar: Adding handler for 0018/0001
oscar: Adding handler for 0018/0007
oscar: Adding handler for 0017/0003
oscar: Adding handler for 0017/0007
oscar: Adding handler for 0017/000a
oscar: Adding handler for 0010/0001
oscar: Adding handler for 0010/0005
oscar: Adding handler for 0009/0001
oscar: Adding handler for 0009/0003
oscar: Adding handler for 0003/0001
oscar: Adding handler for 0003/0003
oscar: Adding handler for 0003/000b
oscar: Adding handler for 0003/000c
oscar: Adding handler for 000e/0001
oscar: Adding handler for 000e/0003
oscar: Adding handler for 000e/0004
oscar: Adding handler for 000e/0002
oscar: Adding handler for 000e/0006
oscar: Adding handler for 000d/0001
oscar: Adding handler for 000d/0009
oscar: Adding handler for 0013/0001
oscar: Adding handler for 0013/0003
oscar: Adding handler for 0013/0006
oscar: Adding handler for 0013/000e
oscar: Adding handler for 0013/0008
oscar: Adding handler for 0013/0015
oscar: Adding handler for 0013/0019
oscar: Adding handler for 0013/001b
oscar: Adding handler for 0013/001c
oscar: Adding handler for 0004/0005
oscar: Adding handler for 0004/0007
oscar: Adding handler for 0004/000a
oscar: Adding handler for 0004/000b
oscar: Adding handler for 0004/0001
oscar: Adding handler for 0004/0014
oscar: Adding handler for 0004/000c
oscar: Adding handler for 0015/00f0
oscar: Adding handler for 0015/00f1
oscar: Adding handler for 0015/00f3
oscar: Adding handler for 0015/00f2
oscar: Adding handler for 0002/0003
oscar: Adding handler for 0002/0006
oscar: Adding handler for 0002/0001
oscar: Adding handler for 0002/fffd
oscar: Adding handler for 0001/0001
oscar: Adding handler for 0001/000f
oscar: Adding handler for 0001/001f
oscar: Adding handler for 0001/0021
oscar: Adding handler for 0001/000a
oscar: Adding handler for 0001/0005
oscar: Adding handler for 0001/0013
oscar: Adding handler for 0001/0010
oscar: Adding handler for 0008/0002
oscar: Adding handler for 000a/0001
oscar: Adding handler for 000a/0003
oscar: oscar_login: gc = 0x84b6b80
dns: DNS query for 'login.oscar.aol.com' queued
account: Connecting to account <my MSN account>
connection: Connecting. gc = 0x84b7948
msn: new httpconn (0x84b7c30)
dns: DNS query for 'messenger.hotmail.com' queued
Session Management: Received first save_yourself
dns: Created new DNS child 30238, there are now 1 children.
*** glibc detected *** gaim: free(): invalid pointer: 0x0811c380 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb735d8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb735da44]
/usr/lib/libotr.so.2[0xb6d0228a]
/usr/lib/libgcrypt.so.11(gcry_free+0x28)[0xb6f9e58b]
/usr/lib/libgcrypt.so.11(gcry_cipher_close+0x84)[0xb6fa3ae8]
/usr/lib/libgnutls.so.13[0xb70dc37d]
/usr/lib/libgnutls.so.13(_gnutls_cipher_deinit+0x21)[0xb70bc541]
/usr/lib/libgnutls.so.13(gnutls_deinit+0xff)[0xb70cfc6f]
/usr/lib/libldap_r.so.2(gnutls_SSL_free+0x2c)[0xb71a351c]
/usr/lib/libldap_r.so.2[0xb71a113f]
/usr/lib/liblber.so.2(ber_sockbuf_remove_io+0x80)[0xb7172e90]
/usr/lib/liblber.so.2(ber_int_sb_destroy+0x4a)[0xb7172f4a]
/usr/lib/liblber.so.2(ber_sockbuf_free+0x34)[0xb7172ff4]
/usr/lib/libldap_r.so.2(ldap_ld_free+0x1b1)[0xb718b5a1]
/lib/libnss_ldap.so.2[0xb71ae170]
/lib/libnss_ldap.so.2[0xb71b1eb9]
/lib/tls/i686/cmov/libc.so.6(fork+0x1de)[0xb738607e]
/lib/tls/i686/cmov/libpthread.so.0(fork+0x14)[0xb76542d4]
/usr/lib/libgaim.so.0[0xb774029e]
/usr/lib/libgaim.so.0[0xb7740895]
/usr/lib/libglib-2.0.so.0[0xb75e0dd6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb75e0802]
/usr/lib/libglib-2.0.so.0[0xb75e37df]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb75e3b89]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c03574]
gaim(main+0x899)[0x80abf49]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb730c8cc]
gaim(gtk_widget_grab_focus+0x35)[0x8067081]
======= Memory map: ========
08048000-080e5000 r-xp 00000000 03:01 9012811    /usr/bin/gaim
080e5000-080e8000 rw-p 0009d000 03:01 9012811    /usr/bin/gaim
080e8000-084d6000 rw-p 080e8000 00:00 0          [heap]
b5600000-b5621000 rw-p b5600000 00:00 0
b5621000-b5700000 ---p b5621000 00:00 0
b57a7000-b5807000 rw-s 00000000 00:08 10780674   /SYSV00000000 (deleted)
b5807000-b581e000 r--s 00000000 03:01 1917052    /var/lib/aspell/en_US-wo_accents-only.rws
b581e000-b5aa6000 r--s 00000000 03:01 1917040    /var/lib/aspell/en-common.rws
b5aa6000-b5aaa000 r-xp 00000000 03:01 9077151    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5aaa000-b5aab000 rw-p 00003000 03:01 9077151    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5aac000-b5b18000 r--p 00000000 03:01 9244209    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5b18000-b5b89000 r--p 00000000 03:01 9244213    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5b89000-b60fa000 r--p 00000000 03:01 9289791    /usr/share/icons/hicolor/icon-theme.cache
b60fa000-b6124000 r-xp 00000000 03:01 9014440    /usr/lib/libkdefx.so.4.2.0
b6124000-b6125000 rw-p 00029000 03:01 9014440    /usr/lib/libkdefx.so.4.2.0
b6125000-b6143000 r-xp 00000000 03:01 9093140    /usr/lib/kde3/plugins/styles/plastik.so
b6143000-b6144000 rw-p 0001e000 03:01 9093140    /usr/lib/kde3/plugins/styles/plastik.so
b6144000-b6155000 r-xp 00000000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6155000-b6156000 rw-p 00010000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6156000-b6174000 r-xp 00000000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6174000-b6175000 rw-p 0001d000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6175000-b61bf000 r-xp 00000000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61bf000-b61c3000 rw-p 00049000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61c3000-b61d8000 r-xp 00000000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d8000-b61d9000 rw-p 00014000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d9000-b696e000 r-xp 00000000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b696e000-b69b5000 rw-p 00794000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b69b5000-b69b8000 rw-p b69b5000 00:00 0
b69c7000-b69e5000 r-xp 00000000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e5000-b69e6000 rw-p 0001e000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e6000-b6a0f000 r-xp 00000000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a0f000-b6a10000 rw-p 00028000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a10000-b6a1e000 r-xp 00000000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1e000-b6a1f000 rw-p 0000e000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1f000-b6a29000 r-xp 00000000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a29000-b6a2a000 rw-p 00009000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a2a000-b6a36000 r-xp 00000000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a36000-b6a37000 rw-p 0000b000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a39000-b6a3b000 r-xp 00000000 03:01 9142361    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6a3b000-b6a3c000 rw-p 00001000 03:01 9142361    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6a3c000-b6a42000 r-xp 00000000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a42000-b6a43000 rw-p 00006000 dns: DNS child 30238 not responding. Killing it!
dnsquery: Unable to send request to resolver process

proxy: Connection attempt failed: Unable to send request to resolver process

oscar: unable to connect FLAP server of type 0x0017
dns: Created new DNS child 30240, there are now 1 children.
*** glibc detected *** gaim: free(): invalid pointer: 0x0811c380 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb735d8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb735da44]
/usr/lib/libotr.so.2[0xb6d0228a]
/usr/lib/libgcrypt.so.11(gcry_free+0x28)[0xb6f9e58b]
/usr/lib/libgcrypt.so.11(gcry_cipher_close+0x84)[0xb6fa3ae8]
/usr/lib/libgnutls.so.13[0xb70dc37d]
/usr/lib/libgnutls.so.13(_gnutls_cipher_deinit+0x21)[0xb70bc541]
/usr/lib/libgnutls.so.13(gnutls_deinit+0xff)[0xb70cfc6f]
/usr/lib/libldap_r.so.2(gnutls_SSL_free+0x2c)[0xb71a351c]
/usr/lib/libldap_r.so.2[0xb71a113f]
/usr/lib/liblber.so.2(ber_sockbuf_remove_io+0x80)[0xb7172e90]
/usr/lib/liblber.so.2(ber_int_sb_destroy+0x4a)[0xb7172f4a]
/usr/lib/liblber.so.2(ber_sockbuf_free+0x34)[0xb7172ff4]
/usr/lib/libldap_r.so.2(ldap_ld_free+0x1b1)[0xb718b5a1]
/lib/libnss_ldap.so.2[0xb71ae170]
/lib/libnss_ldap.so.2[0xb71b1eb9]
/lib/tls/i686/cmov/libc.so.6(fork+0x1de)[0xb738607e]
/lib/tls/i686/cmov/libpthread.so.0(fork+0x14)[0xb76542d4]
/usr/lib/libgaim.so.0[0xb774029e]
/usr/lib/libgaim.so.0[0xb7740895]
/usr/lib/libglib-2.0.so.0[0xb75e0dd6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb75e0802]
/usr/lib/libglib-2.0.so.0[0xb75e37df]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb75e3b89]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c03574]
gaim(main+0x899)[0x80abf49]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb730c8cc]
gaim(gtk_widget_grab_focus+0x35)[0x8067081]
======= Memory map: ========
08048000-080e5000 r-xp 00000000 03:01 9012811    /usr/bin/gaim
080e5000-080e8000 rw-p 0009d000 03:01 9012811    /usr/bin/gaim
080e8000-084d6000 rw-p 080e8000 00:00 0          [heap]
b5600000-b5621000 rw-p b5600000 00:00 0
b5621000-b5700000 ---p b5621000 00:00 0
b57a7000-b5807000 rw-s 00000000 00:08 10780674   /SYSV00000000 (deleted)
b5807000-b581e000 r--s 00000000 03:01 1917052    /var/lib/aspell/en_US-wo_accents-only.rws
b581e000-b5aa6000 r--s 00000000 03:01 1917040    /var/lib/aspell/en-common.rws
b5aa6000-b5aaa000 r-xp 00000000 03:01 9077151    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5aaa000-b5aab000 rw-p 00003000 03:01 9077151    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5aac000-b5b18000 r--p 00000000 03:01 9244209    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5b18000-b5b89000 r--p 00000000 03:01 9244213    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5b89000-b60fa000 r--p 00000000 03:01 9289791    /usr/share/icons/hicolor/icon-theme.cache
b60fa000-b6124000 r-xp 00000000 03:01 9014440    /usr/lib/libkdefx.so.4.2.0
b6124000-b6125000 rw-p 00029000 03:01 9014440    /usr/lib/libkdefx.so.4.2.0
b6125000-b6143000 r-xp 00000000 03:01 9093140    /usr/lib/kde3/plugins/styles/plastik.so
b6143000-b6144000 rw-p 0001e000 03:01 9093140    /usr/lib/kde3/plugins/styles/plastik.so
b6144000-b6155000 r-xp 00000000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6155000-b6156000 rw-p 00010000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6156000-b6174000 r-xp 00000000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6174000-b6175000 rw-p 0001d000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6175000-b61bf000 r-xp 00000000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61bf000-b61c3000 rw-p 00049000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61c3000-b61d8000 r-xp 00000000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d8000-b61d9000 rw-p 00014000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d9000-b696e000 r-xp 00000000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b696e000-b69b5000 rw-p 00794000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b69b5000-b69b8000 rw-p b69b5000 00:00 0
b69c7000-b69e5000 r-xp 00000000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e5000-b69e6000 rw-p 0001e000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e6000-b6a0f000 r-xp 00000000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a0f000-b6a10000 rw-p 00028000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a10000-b6a1e000 r-xp 00000000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1e000-b6a1f000 rw-p 0000e000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1f000-b6a29000 r-xp 00000000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a29000-b6a2a000 rw-p 00009000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a2a000-b6a36000 r-xp 00000000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a36000-b6a37000 rw-p 0000b000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a39000-b6a3b000 r-xp 00000000 03:01 9142361    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6a3b000-b6a3c000 rw-p 00001000 03:01 9142361    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6a3c000-b6a42000 r-xp 00000000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a42000-b6a43000 rw-p 00006000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a43000-b6a45000 r-xp 00000000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a45000-b6a46000 rw-p 00001000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a46000-b6a4d000 r-xp 00000000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4d000-b6a4e000 rw-p 00006000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4e000-b6a50000 r-xp 00000000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a50000-b6a51000 rw-p 00002000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a51000-b6a53000 r-xp 00000000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a53000-b6a54000 rw-p 00001000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a54000-b6a59000 r-xp 00000000 03:01 9225789    /usr/lib/gaim/ticker.so
b6a59000-b6a5a000 rw-p 00004000 03:01 9225789    /usr/lib/gaim/ticker.so
b6a5a000-b6a5b000 r-xp 00000000 03:01 9225779    /usr/lib/gaim/ssl.so
b6a5b000-b6a5c000 rw-p 00000000 03:01 9225779    /usr/lib/gaim/ssl.so
b6a5c000-b6a5d000 r-xp 00000000 03:01 9225768    /usr/lib/gaim/ssl-nss.so
b6a5d000-b6a5e000 rw-p 00000000 03dns: DNS child 30240 not responding. Killing it!
dnsquery: Unable to send request to resolver process

proxy: Connection attempt failed: Unable to send request to resolver process

oscar: unable to connect FLAP server of type 0x0017
*** glibc detected *** gaim: free(): invalid pointer: 0x0811c380 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb735d8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb735da44]
/usr/lib/libotr.so.2[0xb6d0228a]
/usr/lib/libgcrypt.so.11(gcry_free+0x28)[0xb6f9e58b]
/usr/lib/libgcrypt.so.11(gcry_cipher_close+0x84)[0xb6fa3ae8]
/usr/lib/libgnutls.so.13[0xb70dc37d]
/usr/lib/libgnutls.so.13(_gnutls_cipher_deinit+0x21)[0xb70bc541]
/usr/lib/libgnutls.so.13(gnutls_deinit+0xff)[0xb70cfc6f]
/usr/lib/libldap_r.so.2(gnutls_SSL_free+0x2c)[0xb71a351c]
/usr/lib/libldap_r.so.2[0xb71a113f]
/usr/lib/liblber.so.2(ber_sockbuf_remove_io+0x80)[0xb7172e90]
/usr/lib/liblber.so.2(ber_int_sb_destroy+0x4a)[0xb7172f4a]
dns: Created new DNS child 30241, there are now 1 children.
/usr/lib/liblber.so.2(ber_sockbuf_free+0x34)[0xb7172ff4]
/usr/lib/libldap_r.so.2(ldap_ld_free+0x1b1)[0xb718b5a1]
/lib/libnss_ldap.so.2[0xb71ae170]
/lib/libnss_ldap.so.2[0xb71b1eb9]
/lib/tls/i686/cmov/libc.so.6(fork+0x1de)[0xb738607e]
/lib/tls/i686/cmov/libpthread.so.0(fork+0x14)[0xb76542d4]
/usr/lib/libgaim.so.0[0xb774029e]
/usr/lib/libgaim.so.0[0xb7740895]
/usr/lib/libglib-2.0.so.0[0xb75e0dd6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb75e0802]
/usr/lib/libglib-2.0.so.0[0xb75e37df]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb75e3b89]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c03574]
gaim(main+0x899)[0x80abf49]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb730c8cc]
gaim(gtk_widget_grab_focus+0x35)[0x8067081]
======= Memory map: ========
08048000-080e5000 r-xp 00000000 03:01 9012811    /usr/bin/gaim
080e5000-080e8000 rw-p 0009d000 03:01 9012811    /usr/bin/gaim
080e8000-084d6000 rw-p 080e8000 00:00 0          [heap]
b5600000-b5621000 rw-p b5600000 00:00 0
b5621000-b5700000 ---p b5621000 00:00 0
b57a7000-b5807000 rw-s 00000000 00:08 10780674   /SYSV00000000 (deleted)
b5807000-b581e000 r--s 00000000 03:01 1917052    /var/lib/aspell/en_US-wo_accents-only.rws
b581e000-b5aa6000 r--s 00000000 03:01 1917040    /var/lib/aspell/en-common.rws
b5aa6000-b5aaa000 r-xp 00000000 03:01 9077151    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5aaa000-b5aab000 rw-p 00003000 03:01 9077151    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5aac000-b5b18000 r--p 00000000 03:01 9244209    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5b18000-b5b89000 r--p 00000000 03:01 9244213    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5b89000-b60fa000 r--p 00000000 03:01 9289791    /usr/share/icons/hicolor/icon-theme.cache
b60fa000-b6124000 r-xp 00000000 03:01 9014440    /usr/lib/libkdefx.so.4.2.0
b6124000-b6125000 rw-p 00029000 03:01 9014440    /usr/lib/libkdefx.so.4.2.0
b6125000-b6143000 r-xp 00000000 03:01 9093140    /usr/lib/kde3/plugins/styles/plastik.so
b6143000-b6144000 rw-p 0001e000 03:01 9093140    /usr/lib/kde3/plugins/styles/plastik.so
b6144000-b6155000 r-xp 00000000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6155000-b6156000 rw-p 00010000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6156000-b6174000 r-xp 00000000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6174000-b6175000 rw-p 0001d000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6175000-b61bf000 r-xp 00000000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61bf000-b61c3000 rw-p 00049000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61c3000-b61d8000 r-xp 00000000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d8000-b61d9000 rw-p 00014000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d9000-b696e000 r-xp 00000000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b696e000-b69b5000 rw-p 00794000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b69b5000-b69b8000 rw-p b69b5000 00:00 0
b69c7000-b69e5000 r-xp 00000000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e5000-b69e6000 rw-p 0001e000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e6000-b6a0f000 r-xp 00000000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a0f000-b6a10000 rw-p 00028000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a10000-b6a1e000 r-xp 00000000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1e000-b6a1f000 rw-p 0000e000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1f000-b6a29000 r-xp 00000000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a29000-b6a2a000 rw-p 00009000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a2a000-b6a36000 r-xp 00000000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a36000-b6a37000 rw-p 0000b000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a39000-b6a3b000 r-xp 00000000 03:01 9142361    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6a3b000-b6a3c000 rw-p 00001000 03:01 9142361    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6a3c000-b6a42000 r-xp 00000000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a42000-b6a43000 rw-p 00006000 03:01 9225777    /usr/lib/gaim/log_reader.so
b6a43000-b6a45000 r-xp 00000000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a45000-b6a46000 rw-p 00001000 03:01 9225760    /usr/lib/gaim/gnthistory.so
b6a46000-b6a4d000 r-xp 00000000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4d000-b6a4e000 rw-p 00006000 03:01 9225756    /usr/lib/gaim/libbonjour.so
b6a4e000-b6a50000 r-xp 00000000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a50000-b6a51000 rw-p 00002000 03:01 9225757    /usr/lib/gaim/timestamp.so
b6a51000-b6a53000 r-xp 00000000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a53000-b6a54000 rw-p 00001000 03:01 9225770    /usr/lib/gaim/timestamp_format.so
b6a54000-b6a59000 r-xp 00000000 03:01 9225789    /usr/lib/gaim/ticker.so
b6a59000-b6a5a000 rw-p 00004000 03:01 9225789    /udns: DNS child 30241 not responding. Killing it!
dnsquery: Unable to send request to resolver process

proxy: Connection attempt failed: Unable to send request to resolver process

oscar: unable to connect FLAP server of type 0x0017
*** glibc detected *** gaim: free(): invalid pointer: 0x0811c380 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb735d8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb735da44]
/usr/lib/libotr.so.2[0xb6d0228a]
/usr/lib/libgcrypt.so.11(gcry_free+0x28)[0xb6f9e58b]
/usr/lib/libgcrypt.so.11(gcry_cipher_close+0x84)[0xb6fa3ae8]
/usr/lib/libgnutls.so.13[0xb70dc37d]
/usr/lib/libgnutls.so.13(_gnutls_cipher_deinit+0x21)[0xb70bc541]
/usr/lib/libgnutls.so.13(gnutls_deinit+0xff)[0xb70cfc6f]
/usr/lib/libldap_r.so.2(gnutls_SSL_free+0x2c)[0xb71a351c]
/usr/lib/libldap_r.so.2[0xb71a113f]
/usr/lib/liblber.so.2(ber_sockbuf_remove_io+0x80)[0xb7172e90]
/usr/lib/liblber.so.2(ber_int_sb_destroy+0x4adns: Created new DNS child 30242, there are now 1 children.
)[0xb7172f4a]
/usr/lib/liblber.so.2(ber_sockbuf_free+0x34)[0xb7172ff4]
/usr/lib/libldap_r.so.2(ldap_ld_free+0x1b1)[0xb718b5a1]
/lib/libnss_ldap.so.2[0xb71ae170]
/lib/libnss_ldap.so.2[0xb71b1eb9]
/lib/tls/i686/cmov/libc.so.6(fork+0x1de)[0xb738607e]
/lib/tls/i686/cmov/libpthread.so.0(fork+0x14)[0xb76542d4]
/usr/lib/libgaim.so.0[0xb774029e]
/usr/lib/libgaim.so.0[0xb7740895]
/usr/lib/libglib-2.0.so.0[0xb75e0dd6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb75e0802]
/usr/lib/libglib-2.0.so.0[0xb75e37df]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb75e3b89]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c03574]
gaim(main+0x899)[0x80abf49]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb730c8cc]
gaim(gtk_widget_grab_focus+0x35)[0x8067081]
======= Memory map: ========
08048000-080e5000 r-xp 00000000 03:01 9012811    /usr/bin/gaim
080e5000-080e8000 rw-p 0009d000 03:01 9012811    /usr/bin/gaim
080e8000-084d6000 rw-p 080e8000 00:00 0          [heap]
b5600000-b5621000 rw-p b5600000 00:00 0
b5621000-b5700000 ---p b5621000 00:00 0
b57a7000-b5807000 rw-s 00000000 00:08 10780674   /SYSV00000000 (deleted)
b5807000-b581e000 r--s 00000000 03:01 1917052    /var/lib/aspell/en_US-wo_accents-only.rws
b581e000-b5aa6000 r--s 00000000 03:01 1917040    /var/lib/aspell/en-common.rws
b5aa6000-b5aaa000 r-xp 00000000 03:01 9077151    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5aaa000-b5aab000 rw-p 00003000 03:01 9077151    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5aac000-b5b18000 r--p 00000000 03:01 9244209    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5b18000-b5b89000 r--p 00000000 03:01 9244213    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5b89000-b60fa000 r--p 00000000 03:01 9289791    /usr/share/icons/hicolor/icon-theme.cache
b60fa000-b6124000 r-xp 00000000 03:01 9014440    /usr/lib/libkdefx.so.4.2.0
b6124000-b6125000 rw-p 00029000 03:01 9014440    /usr/lib/libkdefx.so.4.2.0
b6125000-b6143000 r-xp 00000000 03:01 9093140    /usr/lib/kde3/plugins/styles/plastik.so
b6143000-b6144000 rw-p 0001e000 03:01 9093140    /usr/lib/kde3/plugins/styles/plastik.so
b6144000-b6155000 r-xp 00000000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6155000-b6156000 rw-p 00010000 03:01 9013987    /usr/lib/libXft.so.2.1.2
b6156000-b6174000 r-xp 00000000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6174000-b6175000 rw-p 0001d000 03:01 9014354    /usr/lib/libjpeg.so.62.0.0
b6175000-b61bf000 r-xp 00000000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61bf000-b61c3000 rw-p 00049000 03:01 9014007    /usr/lib/libXt.so.6.0.0
b61c3000-b61d8000 r-xp 00000000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d8000-b61d9000 rw-p 00014000 03:01 9014083    /usr/lib/libaudio.so.2.4
b61d9000-b696e000 r-xp 00000000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b696e000-b69b5000 rw-p 00794000 03:01 9014829    /usr/lib/libqt-mt.so.3.3.6
b69b5000-b69b8000 rw-p b69b5000 00:00 0
b69c7000-b69e5000 r-xp 00000000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e5000-b69e6000 rw-p 0001e000 03:01 9076868    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b69e6000-b6a0f000 r-xp 00000000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a0f000-b6a10000 rw-p 00028000 03:01 9225788    /usr/lib/gaim/libqq.so
b6a10000-b6a1e000 r-xp 00000000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1e000-b6a1f000 rw-p 0000e000 03:01 9011659    /usr/lib/libavahi-client.so.3.2.0
b6a1f000-b6a29000 r-xp 00000000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a29000-b6a2a000 rw-p 00009000 03:01 9012748    /usr/lib/libavahi-common.so.3.4.2
b6a2a000-b6a36000 r-xp 00000000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a36000-b6a37000 rw-p 0000b000 03:01 9011845    /usr/lib/libhowl.so.0.0.0
b6a39000-b6a3b000 r-xp 00000000 03:01 9142361    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6a3b000-b6a3c000 rw-p 00001000 03:01 9142361    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6a3c000-b6a42000 r-xp 00000000 dns: DNS child 30242 not responding. Killing it!
dnsquery: Unable to send request to resolver process

proxy: Connection attempt failed: Unable to send request to resolver process

msn: Connection error from Notification server (messenger.hotmail.com): Unable to connect
Session Management: Received save_complete
account: Disconnecting account 0x8137c78
connection: Disconnecting connection 0x84b30e8
oscar: Destroying oscar connection of type 0x0017
oscar: Signed off.
connection: Destroying connection 0x84b30e8
account: Disconnecting account 0x814cb00
connection: Disconnecting connection 0x84b48f8
oscar: Destroying oscar connection of type 0x0017
oscar: Signed off.
connection: Destroying connection 0x84b48f8
account: Disconnecting account 0x814e420
connection: Disconnecting connection 0x84b6b80
oscar: Destroying oscar connection of type 0x0017
oscar: Signed off.
connection: Destroying connection 0x84b6b80
account: Disconnecting account 0x815e510
connection: Disconnecting connection 0x84b7948
msn: destroy httpconn (0x84b7c30)
connection: Destroying connection 0x84b7948
docklet: embedded
util: Writing file blist.xml to directory /home/<my user name>/.gaim
util: Writing file accounts.xml to directory /home/<my user name>/.gaim
main: Unloading all plugins
plugins: Unloading plugin Off-the-Record Messaging
g_log: gaim_signal_disconnect: assertion `instance_data != NULL' failed
g_log: gaim_signal_disconnect: assertion `instance_data != NULL' failed
g_log: gaim_signal_disconnect: assertion `instance_data != NULL' failed
g_log: gaim_signal_disconnect: assertion `instance_data != NULL' failed
g_log: gaim_signal_disconnect: assertion `instance_data != NULL' failed
g_log: gaim_signal_disconnect: assertion `instance_data != NULL' failed
plugins: Unloading plugin Gadu-Gadu
plugins: Unloading plugin IRC
plugins: Unloading plugin Jabber
plugins: Unloading plugin MSN
plugins: Unloading plugin GroupWise
plugins: Unloading plugin AIM/ICQ
plugins: Unloading plugin Sametime
plugins: Unloading plugin SIMPLE
plugins: Unloading plugin Yahoo
plugins: Unloading plugin GNUTLS
plugins: Unloading plugin Message Notification
plugins: Unloading plugin Perl Plugin Loader
plugins: Unloading plugin SSL
plugins: Unloading plugin Bonjour
plugins: Unloading plugin GntHistory
plugins: Unloading plugin QQ
Session Management: Handling closed ICE connection... done.
Session Management: Connection closed.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
gtkblist: removed visibility manager: 0
docklet: destroyed


**Finish debug output WITH OTR**

---

### Post by digitalsynthesis on 2006-12-14
**WITHOUT OTR:**

dbus: okkk
plugins: probing /usr/lib/gaim/musicmessaging.so
plugins: probing /usr/lib/gaim/dbus-example.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaimrc.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: /usr/lib/gaim/gevolution.so is not loadable: libedata-book-1.2.so.2: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: probing /usr/lib/gaim/libsametime.so
plugins: /usr/lib/gaim/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
plugins: probing /usr/lib/gaim/libsimple.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is not loadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/perl.so
plugins: probing /usr/lib/gaim/psychic.so
plugins: probing /usr/lib/gaim/relnot.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: /usr/lib/gaim/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/timestamp_format.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/libbonjour.so
plugins: probing /usr/lib/gaim/gnthistory.so
plugins: probing /usr/lib/gaim/gntlastlog.so
plugins: /usr/lib/gaim/gntlastlog.so is not loadable: undefined symbol: cur_term
plugins: probing /usr/lib/gaim/log_reader.so
plugins: probing /usr/lib/gaim/libqq.so
util: Reading file accounts.xml from directory /home/<my user name>/.gaim
util: Reading file status.xml from directory /home/<my user name>/.gaim
stun: using server
stun: using server
sound: Initializing sound output drivers.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
util: Reading file blist.xml from directory /home/<my user name>/.gaim
prefs: Reading /home/<my user name>/.gaim/prefs.xml
prefs: Finished reading /home/<my user name>/.gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/ssl-gnutls.so
plugins: Loading saved plugin /usr/lib/gaim/gnthistory.so
plugins: Loading saved plugin /usr/lib/gaim/notify.so
plugins: Unable to find saved plugin /usr/lib/gaim/gaim-otr.so
plugins: Loading saved plugin /usr/lib/gaim/ssl.so
gtkblist: added visibility manager: 1
docklet: created
pounce: Error reading pounces: Failed to open file '/home/<my user name>/.gaim/pounces.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (KDE) with client ID 107a65726f000116612472800000049800052
Session Management: Using gaim as command
dbus: Need to register an object with the dbus subsystem.
g_log: file ../../libgaim/dbus-server.c: line 118 (gaim_dbus_pointer_to_id): should not be reached
account: Connecting to account < AOL Account 1 >
connection: Connecting. gc = 0x84725e8
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: Adding handler for ffff/0003
oscar: Adding handler for ffff/0006
oscar: Adding handler for 0007/0003
oscar: Adding handler for 0007/0005
oscar: Adding handler for 0007/0007
oscar: Adding handler for 0018/0001
oscar: Adding handler for 0018/0007
oscar: Adding handler for 0017/0003
oscar: Adding handler for 0017/0007
oscar: Adding handler for 0017/000a
oscar: Adding handler for 0010/0001
oscar: Adding handler for 0010/0005
oscar: Adding handler for 0009/0001
oscar: Adding handler for 0009/0003
oscar: Adding handler for 0003/0001
oscar: Adding handler for 0003/0003
oscar: Adding handler for 0003/000b
oscar: Adding handler for 0003/000c
oscar: Adding handler for 000e/0001
oscar: Adding handler for 000e/0003
oscar: Adding handler for 000e/0004
oscar: Adding handler for 000e/0002
oscar: Adding handler for 000e/0006
oscar: Adding handler for 000d/0001
oscar: Adding handler for 000d/0009
oscar: Adding handler for 0013/0001
oscar: Adding handler for 0013/0003
oscar: Adding handler for 0013/0006
oscar: Adding handler for 0013/000e
oscar: Adding handler for 0013/0008
oscar: Adding handler for 0013/0015
oscar: Adding handler for 0013/0019
oscar: Adding handler for 0013/001b
oscar: Adding handler for 0013/001c
oscar: Adding handler for 0004/0005
oscar: Adding handler for 0004/0007
oscar: Adding handler for 0004/000a
oscar: Adding handler for 0004/000b
oscar: Adding handler for 0004/0001
oscar: Adding handler for 0004/0014
oscar: Adding handler for 0004/000c
oscar: Adding handler for 0015/00f0
oscar: Adding handler for 0015/00f1
oscar: Adding handler for 0015/00f3
oscar: Adding handler for 0015/00f2
oscar: Adding handler for 0002/0003
oscar: Adding handler for 0002/0006
oscar: Adding handler for 0002/0001
oscar: Adding handler for 0002/fffd
oscar: Adding handler for 0001/0001
oscar: Adding handler for 0001/000f
oscar: Adding handler for 0001/001f
oscar: Adding handler for 0001/0021
oscar: Adding handler for 0001/000a
oscar: Adding handler for 0001/0005
oscar: Adding handler for 0001/0013
oscar: Adding handler for 0001/0010
oscar: Adding handler for 0008/0002
oscar: Adding handler for 000a/0001
oscar: Adding handler for 000a/0003
oscar: oscar_login: gc = 0x84725e8
dns: DNS query for 'login.oscar.aol.com' queued
account: Connecting to account < AOL Account 2 >
connection: Connecting. gc = 0x8473950
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: Adding handler for ffff/0003
oscar: Adding handler for ffff/0006
oscar: Adding handler for 0007/0003
oscar: Adding handler for 0007/0005
oscar: Adding handler for 0007/0007
oscar: Adding handler for 0018/0001
oscar: Adding handler for 0018/0007
oscar: Adding handler for 0017/0003
oscar: Adding handler for 0017/0007
oscar: Adding handler for 0017/000a
oscar: Adding handler for 0010/0001
oscar: Adding handler for 0010/0005
oscar: Adding handler for 0009/0001
oscar: Adding handler for 0009/0003
oscar: Adding handler for 0003/0001
oscar: Adding handler for 0003/0003
oscar: Adding handler for 0003/000b
oscar: Adding handler for 0003/000c
oscar: Adding handler for 000e/0001
oscar: Adding handler for 000e/0003
oscar: Adding handler for 000e/0004
oscar: Adding handler for 000e/0002
oscar: Adding handler for 000e/0006
oscar: Adding handler for 000d/0001
oscar: Adding handler for 000d/0009
oscar: Adding handler for 0013/0001
oscar: Adding handler for 0013/0003
oscar: Adding handler for 0013/0006
oscar: Adding handler for 0013/000e
oscar: Adding handler for 0013/0008
oscar: Adding handler for 0013/0015
oscar: Adding handler for 0013/0019
oscar: Adding handler for 0013/001b
oscar: Adding handler for 0013/001c
oscar: Adding handler for 0004/0005
oscar: Adding handler for 0004/0007
oscar: Adding handler for 0004/000a
oscar: Adding handler for 0004/000b
oscar: Adding handler for 0004/0001
oscar: Adding handler for 0004/0014
oscar: Adding handler for 0004/000c
oscar: Adding handler for 0015/00f0
oscar: Adding handler for 0015/00f1
oscar: Adding handler for 0015/00f3
oscar: Adding handler for 0015/00f2
oscar: Adding handler for 0002/0003
oscar: Adding handler for 0002/0006
oscar: Adding handler for 0002/0001
oscar: Adding handler for 0002/fffd
oscar: Adding handler for 0001/0001
oscar: Adding handler for 0001/000f
oscar: Adding handler for 0001/001f
oscar: Adding handler for 0001/0021
oscar: Adding handler for 0001/000a
oscar: Adding handler for 0001/0005
oscar: Adding handler for 0001/0013
oscar: Adding handler for 0001/0010
oscar: Adding handler for 0008/0002
oscar: Adding handler for 000a/0001
oscar: Adding handler for 000a/0003
oscar: oscar_login: gc = 0x8473950
dns: DNS query for 'login.oscar.aol.com' queued
account: Connecting to account < AOL Account 3 >
connection: Connecting. gc = 0x8475d60
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: Adding handler for ffff/0003
oscar: Adding handler for ffff/0006
oscar: Adding handler for 0007/0003
oscar: Adding handler for 0007/0005
oscar: Adding handler for 0007/0007
oscar: Adding handler for 0018/0001
oscar: Adding handler for 0018/0007
oscar: Adding handler for 0017/0003
oscar: Adding handler for 0017/0007
oscar: Adding handler for 0017/000a
oscar: Adding handler for 0010/0001
oscar: Adding handler for 0010/0005
oscar: Adding handler for 0009/0001
oscar: Adding handler for 0009/0003
oscar: Adding handler for 0003/0001
oscar: Adding handler for 0003/0003
oscar: Adding handler for 0003/000b
oscar: Adding handler for 0003/000c
oscar: Adding handler for 000e/0001
oscar: Adding handler for 000e/0003
oscar: Adding handler for 000e/0004
oscar: Adding handler for 000e/0002
oscar: Adding handler for 000e/0006
oscar: Adding handler for 000d/0001
oscar: Adding handler for 000d/0009
oscar: Adding handler for 0013/0001
oscar: Adding handler for 0013/0003
oscar: Adding handler for 0013/0006
oscar: Adding handler for 0013/000e
oscar: Adding handler for 0013/0008
oscar: Adding handler for 0013/0015
oscar: Adding handler for 0013/0019
oscar: Adding handler for 0013/001b
oscar: Adding handler for 0013/001c
oscar: Adding handler for 0004/0005
oscar: Adding handler for 0004/0007
oscar: Adding handler for 0004/000a
oscar: Adding handler for 0004/000b
oscar: Adding handler for 0004/0001
oscar: Adding handler for 0004/0014
oscar: Adding handler for 0004/000c
oscar: Adding handler for 0015/00f0
oscar: Adding handler for 0015/00f1
oscar: Adding handler for 0015/00f3
oscar: Adding handler for 0015/00f2
oscar: Adding handler for 0002/0003
oscar: Adding handler for 0002/0006
oscar: Adding handler for 0002/0001
oscar: Adding handler for 0002/fffd
oscar: Adding handler for 0001/0001
oscar: Adding handler for 0001/000f
oscar: Adding handler for 0001/001f
oscar: Adding handler for 0001/0021
oscar: Adding handler for 0001/000a
oscar: Adding handler for 0001/0005
oscar: Adding handler for 0001/0013
oscar: Adding handler for 0001/0010
oscar: Adding handler for 0008/0002
oscar: Adding handler for 000a/0001
oscar: Adding handler for 000a/0003
oscar: oscar_login: gc = 0x8475d60
dns: DNS query for 'login.oscar.aol.com' queued
account: Connecting to account < MSN Account >
connection: Connecting. gc = 0x8476fa8
msn: new httpconn (0x8477140)
dns: DNS query for 'messenger.hotmail.com' queued
Session Management: Received first save_yourself
dns: Created new DNS child 30306, there are now 1 children.
dns: Successfully sent DNS request to child 30306
dns: Created new DNS child 30307, there are now 2 children.
dns: Successfully sent DNS request to child 30307
dns: Created new DNS child 30308, there are now 3 children.
dns: Successfully sent DNS request to child 30308
dns: Created new DNS child 30309, there are now 4 children.
dns: Successfully sent DNS request to child 30309
Session Management: Received save_complete
docklet: embedded
dns: Got response for 'login.oscar.aol.com'
dnsquery: IP resolved for login.oscar.aol.com
proxy: Attempting connection to 64.12.161.185
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
proxy: Connection in progress
dns: Got response for 'login.oscar.aol.com'
dnsquery: IP resolved for login.oscar.aol.com
proxy: Attempting connection to 64.12.161.185
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
proxy: Connection in progress
dns: Got response for 'login.oscar.aol.com'
dnsquery: IP resolved for login.oscar.aol.com
proxy: Attempting connection to 64.12.161.185
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
proxy: Connection in progress
proxy: Connected.
oscar: connected to FLAP server of type 0x0017
oscar: Screen name sent, waiting for response
proxy: Connected.
oscar: connected to FLAP server of type 0x0017
oscar: Screen name sent, waiting for response
proxy: Connected.
oscar: connected to FLAP server of type 0x0017
oscar: Screen name sent, waiting for response
dns: Got response for 'messenger.hotmail.com'
dnsquery: IP resolved for messenger.hotmail.com
proxy: Attempting connection to 65.54.239.210
proxy: Connecting to messenger.hotmail.com:1863 with no proxy
proxy: Connection in progress
oscar: inside auth_resp (Screen name: < AOL Account 1 >)
oscar: Reg status: 1
oscar: E-mail: <my user name>s@pigseye.kennesaw.edu
oscar: BOSIP: 205.188.9.9:5190
oscar: Closing auth connection...
oscar: Scheduling destruction of FLAP connection of type 0x0017
dns: DNS query for '205.188.9.9' queued
oscar: Destroying oscar connection of type 0x0017
dns: Created new DNS child 30310, there are now 1 children.
dns: Successfully sent DNS request to child 30310
dns: Got response for '205.188.9.9'
dnsquery: IP resolved for 205.188.9.9
proxy: Attempting connection to 205.188.9.9
proxy: Connecting to 205.188.9.9:5190 with no proxy
proxy: Connection in progress
oscar: inside auth_resp (Screen name: < AOL Account 3 >)
oscar: Reg status: 1
oscar: E-mail: < AOL Account 3 >@< My Domain >
oscar: BOSIP: 64.12.25.17:5190
oscar: Closing auth connection...
oscar: Scheduling destruction of FLAP connection of type 0x0017
dns: DNS query for '64.12.25.17' queued
oscar: Destroying oscar connection of type 0x0017
dns: Created new DNS child 30311, there are now 1 children.
dns: Successfully sent DNS request to child 30311
oscar: inside auth_resp (Screen name: < AOL Account 2 >)
oscar: Reg status: 3
oscar: E-mail: < My Email >
oscar: BOSIP: 205.188.12.130:5190
oscar: Closing auth connection...
oscar: Scheduling destruction of FLAP connection of type 0x0017
dns: DNS query for '205.188.12.130' queued
dns: Got response for '64.12.25.17'
dnsquery: IP resolved for 64.12.25.17
proxy: Attempting connection to 64.12.25.17
proxy: Connecting to 64.12.25.17:5190 with no proxy
proxy: Connection in progress
dns: Created new DNS child 30312, there are now 1 children.
dns: Successfully sent DNS request to child 30312
proxy: Connected.
oscar: connected to FLAP server of type 0x0002
oscar: Destroying oscar connection of type 0x0017
proxy: Connected.
msn: C: NS 000: VER 1 MSNP9 MSNP8 CVR0
dns: Got response for '205.188.12.130'
dnsquery: IP resolved for 205.188.12.130
proxy: Attempting connection to 205.188.12.130
proxy: Connecting to 205.188.12.130:5190 with no proxy
proxy: Connection in progress
proxy: Connected.
oscar: connected to FLAP server of type 0x0002
proxy: Connected.
oscar: connected to FLAP server of type 0x0002
oscar: MOTD: Unknown (5)
oscar: FLAP connection of type 0x0002 is now fully connected
oscar: ssi: requesting rights and list
oscar: MOTD: Unknown (5)
msn: S: NS 000: VER 1 MSNP9 MSNP8 CVR0
msn: C: NS 000: CVR 2 0x0409 winnt 5.1 i386 MSNMSGR 6.0.0602 MSMSGS < MSN Account >
oscar: MOTD: Unknown (5)
oscar: FLAP connection of type 0x0002 is now fully connected
oscar: ssi: requesting rights and list
oscar: FLAP connection of type 0x0002 is now fully connected
oscar: ssi: requesting rights and list
oscar: locate rights: max sig len = 4096
oscar: buddy list rights: Max buddies = 1000 / Max watchers = 2000
oscar: BOS rights: Max permit = 1000 / Max deny = 1000
connection: Activating keepalive.
oscar: buddy list loaded
oscar: ssi rights: max type 0x0000=3000, max type 0x0001=61, max type 0x0002=1000, max type 0x0003=1000, max type 0x0004=1, max type 0x0005=1, max type 0x0006=150, max type 0x0007=12, max type 0x0008=12, max type 0x0009=3, max type 0x000a=50, max type 0x000b=50, max type 0x000c=0, max type 0x000d=0, max type 0x000e=0, max type 0x000f=0, max type 0x0010=0, max type 0x0011=1, max type 0x0012=0, max type 0x0013=0, max type 0x0014=15, max type 0x0015=1, max type 0x0016=40, max type 0x0017=1, max type 0x0018=10, max type 0x0019=200, max type 0x001a=1, max type 0x001b=0, max type 0x001c=200, max type 0x001d=1, max type 0x001e=8, max type 0x001f=20, max type 0x0020=0, max type 0x0021=10000, max type 0x0022=1000, max type 0x0023=1000,
oscar: ssi: syncing local list and server list
oscar: ssi: activating server-stored buddy list
msn: S: NS 000: CVR 2 7.5.0324 7.5.0324 6.2.0208 [http://msgr.dlservice.microsoft.com/download/5/a/8/5a892c0f-5b87-4767-8927-6fe5d8cfc582/Install_MSN_Messenger.exe](http://msgr.dlservice.microsoft.com/download/5/a/8/5a892c0f-5b87-4767-8927-6fe5d8cfc582/Install_MSN_Messenger.exe) [http://messenger.msn.com](http://messenger.msn.com)
msn: C: NS 000: USR 3 TWN I < MSN Account >
oscar: locate rights: max sig len = 4096
oscar: buddy list rights: Max buddies = 1000 / Max watchers = 2000
oscar: BOS rights: Max permit = 1000 / Max deny = 1000
connection: Activating keepalive.
oscar: buddy list loaded
oscar: ssi rights: max type 0x0000=3000, max type 0x0001=61, max type 0x0002=1000, max type 0x0003=1000, max type 0x0004=1, max type 0x0005=1, max type 0x0006=150, max type 0x0007=12, max type 0x0008=12, max type 0x0009=3, max type 0x000a=50, max type 0x000b=50, max type 0x000c=0, max type 0x000d=0, max type 0x000e=0, max type 0x000f=0, max type 0x0010=0, max type 0x0011=1, max type 0x0012=0, max type 0x0013=0, max type 0x0014=15, max type 0x0015=1, max type 0x0016=40, max type 0x0017=1, max type 0x0018=10, max type 0x0019=200, max type 0x001a=1, max type 0x001b=0, max type 0x001c=200, max type 0x001d=1, max type 0x001e=8, max type 0x001f=20, max type 0x0020=0, max type 0x0021=10000, max type 0x0022=1000, max type 0x0023=1000,
oscar: ssi: syncing local list and server list
oscar: ssi: activating server-stored buddy list
oscar: locate rights: max sig len = 4096
oscar: buddy list rights: Max buddies = 1000 / Max watchers = 2000
oscar: BOS rights: Max permit = 1000 / Max deny = 1000
connection: Activating keepalive.
oscar: buddy list loaded
oscar: ssi rights: max type 0x0000=3000, max type 0x0001=61, max type 0x0002=1000, max type 0x0003=1000, max type 0x0004=1, max type 0x0005=1, max type 0x0006=150, max type 0x0007=12, max type 0x0008=12, max type 0x0009=3, max type 0x000a=50, max type 0x000b=50, max type 0x000c=0, max type 0x000d=0, max type 0x000e=0, max type 0x000f=0, max type 0x0010=0, max type 0x0011=1, max type 0x0012=0, max type 0x0013=0, max type 0x0014=15, max type 0x0015=1, max type 0x0016=40, max type 0x0017=1, max type 0x0018=10, max type 0x0019=200, max type 0x001a=1, max type 0x001b=0, max type 0x001c=200, max type 0x001d=1, max type 0x001e=8, max type 0x001f=20, max type 0x0020=0, max type 0x0021=10000, max type 0x0022=1000, max type 0x0023=1000,
oscar: ssi: syncing local list and server list
oscar: ssi: activating server-stored buddy list
oscar: Connecting to FLAP server 205.188.248.168:5190 of type 0x0018
dns: DNS query for '205.188.248.168' queued
dns: Created new DNS child 30313, there are now 1 children.
dns: Successfully sent DNS request to child 30313
oscar: Connecting to FLAP server 205.188.176.105:5190 of type 0x000d
dns: DNS query for '205.188.176.105' queued
dns: Got response for '205.188.248.168'
dnsquery: IP resolved for 205.188.248.168
proxy: Attempting connection to 205.188.248.168
proxy: Connecting to 205.188.248.168:5190 with no proxy
proxy: Connection in progress
dns: Created new DNS child 30314, there are now 1 children.
dns: Successfully sent DNS request to child 30314
buddyicon: Wrote file /home/<my user name>/.gaim/icons/38b29b08
buddyicon: Uncached file 3f5b52cf
< SNIP BUDDY DATA >
dns: DNS query for '205.188.176.69' queued
proxy: Connected.
oscar: connected to FLAP server of type 0x0018
dns: Created new DNS child 30315, there are now 1 children.
dns: Successfully sent DNS request to child 30315
dns: Created new DNS child 30316, there are now 2 children.
dns: Successfully sent DNS request to child 30316
dns: Created new DNS child 30317, there are now 3 children.
dns: Successfully sent DNS request to child 30317
dns: Created new DNS child 30318, there are now 4 children.
dns: Successfully sent DNS request to child 30318
proxy: Connected.
oscar: connected to FLAP server of type 0x000d
dns: Got response for '207.46.109.93'
dnsquery: IP resolved for 207.46.109.93
proxy: Attempting connection to 207.46.109.93
proxy: Connecting to 207.46.109.93:1863 with no proxy
proxy: Connection in progress
dns: Created new DNS child 30319, there are now 4 children.
dns: Successfully sent DNS request to child 30319
dns: Got response for '64.12.165.99'
dnsquery: IP resolved for 64.12.165.99
proxy: Attempting connection to 64.12.165.99
proxy: Connecting to 64.12.165.99:5190 with no proxy
proxy: Connection in progress
dns: Got response for '205.188.176.103'
dnsquery: IP resolved for 205.188.176.103
proxy: Attempting connection to 205.188.176.103
proxy: Connecting to 205.188.176.103:5190 with no proxy
proxy: Connection in progress
dns: Got response for '64.12.160.149'
dnsquery: IP resolved for 64.12.160.149
proxy: Attempting connection to 64.12.160.149
proxy: Connecting to 64.12.160.149:5190 with no proxy
proxy: Connection in progress
dns: Got response for '205.188.176.69'
dnsquery: IP resolved for 205.188.176.69
proxy: Attempting connection to 205.188.176.69
proxy: Connecting to 205.188.176.69:5190 with no proxy
proxy: Connection in progress
proxy: Connected.
oscar: connected to FLAP server of type 0x0018
proxy: Connected.
oscar: connected to FLAP server of type 0x0018
proxy: Connected.
oscar: connected to FLAP server of type 0x000d
oscar: FLAP connection of type 0x0018 is now fully connected
proxy: Connected.
msn: C: NS 000: VER 4 MSNP9 MSNP8 CVR0
proxy: Connected.
oscar: connected to FLAP server of type 0x000d
oscar: FLAP connection of type 0x000d is now fully connected
oscar: FLAP connection of type 0x0018 is now fully connected
oscar: FLAP connection of type 0x0018 is now fully connected
msn: S: NS 000: VER 4 MSNP9 MSNP8 CVR0
msn: < SNIP DATA >
oscar: FLAP connection of type 0x000d is now fully connected
oscar: chat info: Chat Rights:
oscar: chat info:       Max Concurrent Rooms: 10
oscar: chat info:       Exchange List: (16 total)
oscar: chat info:               20
oscar: chat info:               16
oscar: chat info:               15
oscar: chat info:               14
oscar: chat info:               13
oscar: chat info:               12
oscar: chat info:               11
oscar: chat info:               10
oscar: chat info:               9
oscar: chat info:               8
oscar: chat info:               7
oscar: chat info:               6
oscar: chat info:               5
oscar: chat info:               4
oscar: chat info:               2
oscar: chat info:               1
oscar: FLAP connection of type 0x000d is now fully connected
msn: S: NS 000: CVR 5 7.5.0324 7.5.0324 6.2.0208 [http://msgr.dlservice.microsoft.com/download/5/a/8/5a892c0f-5b87-4767-8927-6fe5d8cfc582/Install_MSN_Messenger.exe](http://msgr.dlservice.microsoft.com/download/5/a/8/5a892c0f-5b87-4767-8927-6fe5d8cfc582/Install_MSN_Messenger.exe) [http://messenger.msn.com](http://messenger.msn.com)
msn: < SNIP DATA >
oscar: chat info: Chat Rights:
oscar: chat info:       Max Concurrent Rooms: 10
oscar: chat info:       Exchange List: (16 total)
oscar: chat info:               20
oscar: chat info:               16
oscar: chat info:               15
oscar: chat info:               14
oscar: chat info:               13
oscar: chat info:               12
oscar: chat info:               11
oscar: chat info:               10
oscar: chat info:               9
oscar: chat info:               8
oscar: chat info:               7
oscar: chat info:               6
oscar: chat info:               5
oscar: chat info:               4
oscar: chat info:               2
oscar: chat info:               1
oscar: chat info: Chat Rights:
oscar: chat info:       Max Concurrent Rooms: 10
oscar: chat info:       Exchange List: (16 total)
oscar: chat info:               20
oscar: chat info:               16
oscar: chat info:               15
oscar: chat info:               14
oscar: chat info:               13
oscar: chat info:               12
oscar: chat info:               11
oscar: chat info:               10
oscar: chat info:               9
oscar: chat info:               8
oscar: chat info:               7
oscar: chat info:               6
oscar: chat info:               5
oscar: chat info:               4
oscar: chat info:               2
oscar: chat info:               1
msn: < SNIP DATA >
dns: DNS query for 'nexus.passport.com' queued
dns: Created new DNS child 30320, there are now 1 children.
dns: Successfully sent DNS request to child 30320
oscar: Connecting to FLAP server 64.12.31.84:5190 of type 0x0010
dns: DNS query for '64.12.31.84' queued
dns: Created new DNS child 30321, there are now 2 children.
dns: Successfully sent DNS request to child 30321
dns: Got response for '64.12.31.84'
dnsquery: IP resolved for 64.12.31.84
proxy: Attempting connection to 64.12.31.84
proxy: Connecting to 64.12.31.84:5190 with no proxy
proxy: Connection in progress
proxy: Connected.
oscar: connected to FLAP server of type 0x0010
dns: Got response for 'nexus.passport.com'
dnsquery: IP resolved for nexus.passport.com
proxy: Attempting connection to 65.54.179.228
proxy: Connecting to nexus.passport.com:443 with no proxy
proxy: Connection in progress
oscar: Connecting to FLAP server 205.188.1.116:5190 of type 0x0010
dns: DNS query for '205.188.1.116' queued
dns: Created new DNS child 30322, there are now 1 children.
dns: Successfully sent DNS request to child 30322
oscar: FLAP connection of type 0x0010 is now fully connected
dns: Got response for '205.188.1.116'
dnsquery: IP resolved for 205.188.1.116
proxy: Attempting connection to 205.188.1.116
proxy: Connecting to 205.188.1.116:5190 with no proxy
proxy: Connection in progress
proxy: Connected.
oscar: connected to FLAP server of type 0x0010
proxy: Connected.
gnutls: Handshaking
oscar: FLAP connection of type 0x0010 is now fully connected
gnutls: Handshaking
gnutls: Handshaking
gnutls: Handshake complete
dns: DNS query for 'login.live.com' queued
dns: Created new DNS child 30323, there are now 1 children.
dns: Successfully sent DNS request to child 30323
dns: Got response for 'login.live.com'
dnsquery: IP resolved for login.live.com
proxy: Attempting connection to 65.54.183.202
proxy: Connecting to login.live.com:443 with no proxy
proxy: Connection in progress
proxy: Connected.
gnutls: Handshaking
gnutls: Handshaking
oscar: no more icons to request
gnutls: Handshaking
gnutls: Handshake complete

<SNIP ACCOUNT DATA>

account: Disconnecting account 0x8137998
connection: Disconnecting connection 0x84725e8
connection: Deactivating keepalive.
oscar: Destroying oscar connection of type 0x0010
oscar: Destroying oscar connection of type 0x000d
oscar: Destroying oscar connection of type 0x0018
oscar: Destroying oscar connection of type 0x0002
oscar: Signed off.
connection: Destroying connection 0x84725e8
account: Disconnecting account 0x814b9d8
connection: Disconnecting connection 0x8473950
connection: Deactivating keepalive.
oscar: Destroying oscar connection of type 0x000d
oscar: Destroying oscar connection of type 0x0018
oscar: Destroying oscar connection of type 0x0002
oscar: Signed off.
connection: Destroying connection 0x8473950
account: Disconnecting account 0x814d358
connection: Disconnecting connection 0x8475d60
connection: Deactivating keepalive.
oscar: Destroying oscar connection of type 0x0010
oscar: Destroying oscar connection of type 0x000d
oscar: Destroying oscar connection of type 0x0018
oscar: Destroying oscar connection of type 0x0002
oscar: Signed off.
connection: Destroying connection 0x8475d60
account: Disconnecting account 0x815dc98
connection: Disconnecting connection 0x8476fa8
connection: Deactivating keepalive.
msn: C: NS 000: OUT
msn: destroy httpconn (0x8477140)
connection: Destroying connection 0x8476fa8
util: Writing file blist.xml to directory /home/<my user name>/.gaim
util: Writing file accounts.xml to directory /home/<my user name>/.gaim
main: Unloading all plugins
plugins: Unloading plugin Gadu-Gadu
plugins: Unloading plugin IRC
plugins: Unloading plugin Jabber
plugins: Unloading plugin MSN
plugins: Unloading plugin GroupWise
plugins: Unloading plugin AIM/ICQ
plugins: Unloading plugin Sametime
plugins: Unloading plugin SIMPLE
plugins: Unloading plugin Yahoo
plugins: Unloading plugin GNUTLS
plugins: Unloading plugin Message Notification
plugins: Unloading plugin Perl Plugin Loader
plugins: Unloading plugin SSL
plugins: Unloading plugin Bonjour
plugins: Unloading plugin GntHistory
plugins: Unloading plugin QQ
Session Management: Handling closed ICE connection... done.
Session Management: Connection closed.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
gtkblist: removed visibility manager: 0
docklet: destroyed


**Finish WITHOUT OTR**

---

