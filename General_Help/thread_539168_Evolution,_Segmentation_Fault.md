---
title: "Evolution, Segmentation Fault"
date: 2007-08-30
forum: General Help
---

### Post by moore.bryan on 2007-08-30
[I]alright friends; i'm at a loss.  yesterday, evolution worked perfectly.  today, without upgrading/installing/changing anything, i now get this:
```

moore@ubuntu:~$ evolution --disable-eplugin --offline

(evolution-2.10:1585): evolution-smime-WARNING **: initializing security library without cert databases.

(evolution-2.10:1585): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:1585): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:1585): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `ESourceGroup'

(evolution-2.10:1585): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion `E_IS_SOURCE_GROUP (group)' failed
Segmentation fault

```
when i run it as root, it starts and i get this:
```
moore@ubuntu:~$ gksudo evolution
CalDAV Eplugin starting up ...

(evolution-2.10:3090): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
/bin/sh: /usr/bin/esd: not found
```
huh?
[/I]

---

### Post by moore.bryan on 2007-08-31
*no one?*

---

### Post by moore.bryan on 2007-09-01
[I]well, thanks a lot guys/gals!  ;-)

somehow, and i'm not really sure how, i've gotten it to work.  i wish i knew what i did to make it happen, so as to help others, but no dice.
[/I]

---

### Post by freelsjd on 2007-09-06
today, from both ubuntu/feisty and debian/etch servers, evolution starts up withe following error and dies:  I think it is some kind of exchange server error:

CalDAV Eplugin starting up ...

(evolution-2.10:3606): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

evolution

(evolution-2.10:3606): libsoup-CRITICAL **: soup_message_set_flags: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution-2.10:3606): libsoup-CRITICAL **: soup_session_send_message: assertion `SOUP_IS_MESSAGE (msg)' failed
Segmentation fault

---

### Post by pagingmrherman on 2007-09-18
I got the same thing when we replaced the SSL cert for OWA.  Still can't find a solution.

---

### Post by stchman on 2007-09-18
> **moore.bryan said:**
> [I]alright friends; i'm at a loss.  yesterday, evolution worked perfectly.  today, without upgrading/installing/changing anything, i now get this:
```

moore@ubuntu:~$ evolution --disable-eplugin --offline

(evolution-2.10:1585): evolution-smime-WARNING **: initializing security library without cert databases.

(evolution-2.10:1585): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:1585): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:1585): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `ESourceGroup'

(evolution-2.10:1585): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion `E_IS_SOURCE_GROUP (group)' failed
Segmentation fault

```
when i run it as root, it starts and i get this:
```
moore@ubuntu:~$ gksudo evolution
CalDAV Eplugin starting up ...

(evolution-2.10:3090): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
/bin/sh: /usr/bin/esd: not found
```
huh?
[/I]

My friend had this happen when he received a strangely formatted message.

---

### Post by mikawber on 2007-10-28
I'm getting this same issue, and I can't fix it. I've tried unintslling evolution completely and it doesn't solve the issue. Anybody know how?

---

### Post by mikawber on 2007-10-29
I just managed to get this to work about 5 minutes ago. First I removed evolution, then all I had to do is run the following commands:
```
rm -r ~/.gconf/apps/evolution/
gconftool-2 --recursive-unset /apps/evolution
```

After that I reinstalled evolution and it started working perfectly.

---

### Post by bodybuzz on 2007-10-29
Dear god i wanted this to work but I am having the same crash/explosion when i try to add/authenticate to the exchange server..   :cry: WAAAHHHH :cry:

---

### Post by croc1 on 2007-11-12
> **mikawber said:**
> I just managed to get this to work about 5 minutes ago. First I removed evolution, then all I had to do is run the following commands:
```
rm -r ~/.gconf/apps/evolution/
gconftool-2 --recursive-unset /apps/evolution
```

After that I reinstalled evolution and it started working perfectly.

Thanks had  the same problem 
This worked :lolflag:

---

### Post by vivabenfica on 2007-11-19
i've always had evolution problems with exchange, but never this:

slb@Catedral:/media/disk/savior$ evolution

(evolution:20644): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
commit
** (evolution:20644): DEBUG: mailto URL command: mozilla-thunderbird %s
** (evolution:20644): DEBUG: mailto URL program: mozilla-thunderbird

(evolution:20644): e-utils-WARNING **: No parent set, or default parent available for error dialog
old group, new source
*** glibc detected *** evolution: double free or corruption (fasttop): 0xac749010 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6db4d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6db8800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb6ecb961]
/usr/lib/libcamel-provider-1.2.so.10[0xb7d98f6d]
/usr/lib/libcamel-provider-1.2.so.10(camel_message_info_free+0xa1)[0xb7d99051]
/usr/lib/evolution-data-server-1.2/camel-providers-10/libcamellocal.so[0xb10ba2e7]
/usr/lib/libcamel-provider-1.2.so.10[0xb7d9d0b6]
/usr/lib/evolution-data-server-1.2/camel-providers-10/libcamellocal.so[0xb10b8400]
/usr/lib/libcamel-provider-1.2.so.10(camel_folder_summary_info_new_from_parser+0x7a)[0xb7d9baaa]
/usr/lib/libcamel-provider-1.2.so.10(camel_folder_summary_add_from_parser+0x56)[0xb7d9cbe6]
/usr/lib/evolution-data-server-1.2/camel-providers-10/libcamellocal.so[0xb10b9c28]
/usr/lib/evolution-data-server-1.2/camel-providers-10/libcamellocal.so[0xb10ba4f8]
/usr/lib/evolution-data-server-1.2/camel-providers-10/libcamellocal.so(camel_local_summary_check+0x47)[0xb10b4337]
/usr/lib/evolution-data-server-1.2/camel-providers-10/libcamellocal.so[0xb10b2883]
/usr/lib/libcamel-provider-1.2.so.10(camel_folder_refresh_info+0x3e)[0xb7da121e]
/usr/lib/evolution/2.12/components/libevolution-mail.so[0xb6347ad7]
/usr/lib/evolution/2.12/components/libevolution-mail.so[0xb6344405]
/usr/lib/libedataserver-1.2.so.9[0xb7bd1660]
/lib/tls/i686/cmov/libpthread.so.0[0xb7c8946b]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb6e1e6de]
======= Memory map: ========
08048000-08064000 r-xp 00000000 08:06 416332     /usr/bin/evolution
08064000-08066000 rw-p 0001c000 08:06 416332     /usr/bin/evolution
08066000-08bef000 rw-p 08066000 00:00 0          [heap]
abeff000-abf00000 ---p abeff000 00:00 0 
abf00000-ac76a000 rw-p abf00000 00:00 0 
ac76a000-ac800000 ---p ac76a000 00:00 0 
ac8fd000-ac8fe000 ---p ac8fd000 00:00 0 
ac8fe000-ad0fe000 rw-p ac8fe000 00:00 0 
ad0fe000-ad0ff000 ---p ad0fe000 00:00 0 
ad0ff000-ad8ff000 rw-p ad0ff000 00:00 0 
ad8ff000-ad900000 ---p ad8ff000 00:00 0 
ad900000-ae1ac000 rw-p ad900000 00:00 0 
ae1ac000-ae200000 ---p ae1ac000 00:00 0 
ae2ab000-ae2ac000 ---p ae2ab000 00:00 0 
ae2ac000-aeaac000 rw-p ae2ac000 00:00 0 
aeaac000-aeaad000 ---p aeaac000 00:00 0 
aeaad000-af2ad000 rw-p aeaad000 00:00 0 
af2ad000-af2ae000 ---p af2ad000 00:00 0 
af2ae000-afaae000 rw-p af2ae000 00:00 0 
afaae000-afaaf000 ---p afaae000 00:00 0 
afaaf000-b02af000 rw-p afaaf000 00:00 0 
b0401000-b0402000 ---p b0401000 00:00 0 
b0402000-b0c02000 rw-p b0402000 00:00 0 
b0c02000-b0c62000 rw-s 00000000 00:09 6357006    /SYSV00000000 (deleted)
b0c62000-b0c71000 r-xp 00000000 08:06 1235495    /lib/libbz2.so.1.0.4
b0c71000-b0c72000 rw-p 0000f000 08:06 1235495    /lib/libbz2.so.1.0.4
b0c72000-b0ca4000 r-xp 00000000 08:06 407621     /usr/lib/libcroco-0.6.so.3.0.1
b0ca4000-b0ca7000 rw-p 00031000 08:06 407621     /usr/lib/libcroco-0.6.so.3.0.1
b0ca7000-b0cd7000 r-xp 00000000 08:06 407813     /usr/lib/libgsf-1.so.114.0.7
b0cd7000-b0cda000 rw-p 0002f000 08:06 407813     /usr/lib/libgsf-1.so.114.0.7
b0cda000-b0cdb000 rw-p b0cda000 00:00 0 
b0cdb000-b0d0b000 r-xp 00000000 08:06 408077     /usr/lib/librsvg-2.so.2.18.2
b0d0b000-b0d0c000 rw-p 00030000 08:06 408077     /usr/lib/librsvg-2.so.2.18.2
b0d1c000-b0d1d000 r-xp 00000000 08:06 455443     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b0d1d000-b0d1e000 rw-p 00000000 08:06 455443     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b0d1e000-b0da2000 r--p 00000000 08:06 570345     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b0de6000-b0dea000 r-xp 00000000 08:06 17142      /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b0dea000-b0dec000 rw-p 00003000 08:06 17142      /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b0dec000-b0dee000 r-xp 00000000 08:06 1235550    /lib/libnss_mdns4_minimal.so.2
b0dee000-b0def000 rw-p 00001000 08:06 1235550    /lib/libnss_mdns4_minimal.so.2
b0e3d000-b0e47000 r-xp 00000000 08:06 1235523    /lib/libgcc_s.so.1
b0e47000-b0e48000 rw-p 0000a000 08:06 1235523    /lib/libgcc_s.so.1
b0e58000-b0e68000 r-xp 00000000 08:06 146761     /usr/lib/gconv/libGB.so
b0e68000-b0e6a000 rw-p 0000f000 08:06 146761     /usr/lib/gconv/libGB.so
b0e6a000-b0e6d000 r-xp 00000000 08:06 146588     /usr/lib/gconv/EUC-CN.so
b0e6d000-b0e6f000 rw-p 00002000 08:06 146588     /usr/lib/gconv/EUC-CN.so
b0e6f000-b0e83000 r-xp 00000000 08:06 587805     /usr/lib/evolution/2.12/plugins/liborg-gnome-groupwise-features.so
b0e83000-b0e84000 rw-p 00014000 08:06 587805     /usr/lib/evolution/2.12/plugins/liborg-gnome-groupwise-features.so
b0e84000-b0e85000 r-xp 00000000 08:06 587921     /usr/lib/evolution/2.12/plugins/liborg-gnome-new-mail-notify.so
b0e85000-b0e86000 rw-p 00000000 08:06 587921     /usr/lib/evolution/2.12/plugins/liborg-gnome-new-mail-notify.so
b0e86000-b0e88000 r-xAborted (core dumped)
slb@Catedral:/media/disk/savior$ cp -rf .evolution/ ~/

---

### Post by chudder on 2008-01-02
> **mikawber said:**
> I just managed to get this to work about 5 minutes ago. First I removed evolution, then all I had to do is run the following commands:
```
rm -r ~/.gconf/apps/evolution/
gconftool-2 --recursive-unset /apps/evolution
```

After that I reinstalled evolution and it started working perfectly.

This worked for me too! thanx a ton!  I still don't understand why it happens, if someone could give me a rundown of what's going on that would be great!

Chudder

---

