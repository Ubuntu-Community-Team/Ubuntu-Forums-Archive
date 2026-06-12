---
title: "[SOLVED] Session last 10 secs and logs out?!?! WTL (wat the linux)"
date: 2007-07-30
forum: General Help
---

### Post by hwshadow on 2007-07-30
Ok ive had Ubuntu for about 2 months now and i think i have run into this twice 
and i need to know what is why my computer logins on gets a 10 second session message, and then logs out heres what the .xsession log says.   It would be much appreciated is someone could explain to me what is the most likely cause and how to fix it or at least point me in the right direction, cause i have googled this till im blue in the face.  Anyways it was working fine, i went up stairs to watch a move we had rented fell asleep on the floor, and woke up, and was greeted by this nasty little message.  And if it helps any i do have root login enabled.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "hwshadow"
/etc/gdm/Xsession: Beginning session setup...
No profile for user 'hwshadow' found
SESSION_MANAGER=local/UNIXISDABOMB:/tmp/.ICE-unix/8790
Initializing gnome-mount extension
seahorse nautilus module initialized

(update-notifier:8890): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

oh i also have compiz-fusion install could that be causing this or at least contribute?
i would like some way that doesnt require reformating cause i did that the first time... and well i spent 2 days customizing, updating, and installing stuff so please help if u can.

---

### Post by hwshadow on 2007-08-06
n oone can help me :sad:?!?   I havent had a single post with 44 views so wat did i post this in the wrong section or wat. Plz id like to get this fixed i spent like 2 days customizing every thing and i had it updating and i was told we had a power outage in the middle of that night some maybe thats why its messed up.  I dont know but if any one can help me fix it and not have to reformat that would be great cause i dont like using windows as much as ubuntu and well im having to use windows so :lolflag: help me please :D

---

### Post by kevindontenville on 2007-08-06
try booting into recovery mode from the boot menu and seeing if there are problems booting. The recovery mode takes you in as root to a console session. Could be a disk error that may be picked up during boot to recovery.

Sounds to me like it could be the general profile in /etc/profile or possible the .profile in the user home directory is damaged. Had issues similar with ownership changes on home directories or missing/damaged home directories.

Any help?

---

### Post by hwshadow on 2007-08-07
omg Thanks so much for replying ive been waiting a week with my :popcorn: :lolflag:.  Ya i dont think its an error with my harddrives cause the are 1 month old SATA 500gb bussiness class, i think it was a mini power outage that caused it.  Thank you for giving me a place to start lol cause right now unix is almost entirely greek to me as i just switched and dont know all wat does wat and *continues in to a wordlessness end :lolflag:* 

anyways ill try those and get back to you ( just got back from work)

and again thanks for the reply!!!:):KS:)

---

### Post by kevindontenville on 2007-08-07
I know what its like to feel like a newbie and all alone with a Linux console staring at you from the screen ;-) - Although that's very rare on these forums they are a friendly bunch!

The reason I suggested possible disk error wasn't due to a physical failure of the disks but the problems a power outage can create - spikes, part written data, cache corruption etc common to basically all OS and most hardware. I cheat a bit and use a massive UPS on my systems to save PSUs and data ;-)

Good luck and do let us know what happens, might help someone else later!

---

### Post by hwshadow on 2007-08-08
can u by any chance tell me wat the .profile file is suppose to look like cause both are there, and dont seem to be damaged  i check the xsession log again and it seems to be getting longer.  The funny thing is i can log onto the fubared account at use it as normal if i ignore the xsession error popup once i touch that it boots me out and logs me off, i can even use compiz fusion with the pop on and surf the web as long as i dont close the xsession log  its really weird.  any ways heres the 2 profile files and the new xsession log.  and it look as if i have to reformat ;(

**_profile in etc/_**
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
 
=-----------------------=
end

[U][B]
.profile in home folder[/B][/U]
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

=-------------------=
end

[U][B]
X Session [/B][/U]
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "hwshadow"
/etc/gdm/Xsession: Beginning session setup...
No profile for user 'hwshadow' found
SESSION_MANAGER=local/UNIXISDABOMB:/tmp/.ICE-unix/5819
Initializing gnome-mount extension
*** glibc detected *** x-session-manager: malloc(): memory corruption (fast): 0x0826f398 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76496fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb764a60e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb77602c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7af5db0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7af71e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7afaf2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7afb1c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7afb27f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_.widget_queue_draw_area+0x150)[0xb7db0440]
x-session-manager[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb77593c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7758df2]
/usr/lib/libglib-2.0.so.0[0xb775bdcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb775c179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c90044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75f6ebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:02 10634324   /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:02 10634324   /usr/bin/gnome-session
08069000-082ac000 rw-p 08069000 00:00 0          [heap]
b4300000-b4321000 rw-p b4300000 00:00 0 
b4321000-b4400000 ---p b4321000 00:00 0 
b4459000-b4464000 r-xp 00000000 08:02 2932800    /lib/libgcc_s.so.1
b4464000-b4465000 rw-p 0000a000 08:02 2932800    /lib/libgcc_s.so.1
b4474000-b4475000 ---p b4474000 00:00 0 
b4475000-b4c75000 rw-p b4475000 00:00 0 
b4c75000-b4cf2000 r--p 00000000 08:02 10895492   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4cf2000-b4cf4000 r-xp 00000000 08:02 10765499   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4cf4000-b4cf5000 rw-p 00001000 08:02 10765499   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4cf5000-b4cfb000 r--s 00000000 08:02 4259932    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4cfb000-b4cfc000 r--s 00000000 08:02 4262017    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b4cfc000-b4cff000 r--s 00000000 08:02 4262015    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b4cff000-b4d00000 r--s 00000000 08:02 4262014    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b4d00000-b4d01000 r--s 00000000 08:02 4262012    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b4d01000-b4d05000 r--s 00000000 08:02 4259929    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b4d05000-b4d06000 r--s 00000000 08:02 4261880    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4d06000-b4d08000 r--s 00000000 08:02 4261807    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b4d08000-b4d0a000 r--s 00000000 08:02 4261806    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b4d0a000-b4d0b000 r--s 00000000 08:02 4261805    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b4d0b000-b4d0d000 r--s 00000000 08:02 4261803    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b4d0d000-b4d13000 r--s 00000000 08:02 4261802    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4d13000-b4d15000 r--s 00000000 08:02 4261801    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4d15000-b4d17000 r--s 00000000 08:02 4261798    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b4d17000-b4d1f000 r--s 00000000 08:02 4261797    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4d1f000-b4d25000 r--s 00000000 08:02 4261727    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4d25000-b4d26000 r--s 00000000 08:02 4261726    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4d26000-b4d28000 r--s 00000000 08:02 4261725    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4d28000-b4d2e000 r--s 00000000 08:02 4261723    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4d2e000-b4d31000 r--s 00000000 08:02 4261700    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b4d31000-b4d35000 r--s 00000000 08:02 4259914    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4d35000-b4d37000 r--s 00000000 08:02 4261684    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4d37000-b4d38000 r--s 00000000 08:02 4262538    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b4d38000-b4d39000 r--s 00000000 08:02 4262537    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b4d39000-b4d3a000 r--s 00000000 08:02 4262536    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b4d3a000-b4d3b000 r--s 00000000 08:02 4262535    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b4d3b000-b4d3c000 r--s 00000000 08:02 4262534    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4d3c000-b4d3f000 r--s 00000000 08:02 4262533    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4d3f000-b4d44000 r--s 00000000 08:02 4262531    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4d44000-b4d46000 r--s 00000000 08:02 4262503    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4d46000-b4d47000 r--s 00000000 08:02 4262502    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4d47000-b4d49000 r--s 00000000 08:02 4262485    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4d49000-b4d4a000 r--s 00000000 08:02 4262480    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4d4a000-b4d4f000 r--s 00000000 08:02 4262478    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4d4f000-b4d53000 r--s 00000000 08:02 4262450    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b4d53000-b4d55000 r--s 00000000 08:02 4262448    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b4d55000-b4d58000 r--s 00000000 08:02 4262446    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4d58000-b4d59000 r--s 00000000 08:02 4262400    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b4d59000-b4d5b000 r--s 00000000 08:02 4262399    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b4d5b000-b4d5f000 r--s 00000000 08:02 4262397    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b4d5f000-b4d65000 r--s 00000000 08:02 4262392    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4d65000-b4d66000 r--s 00000000 08:02 4262188    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b4d66000-b4d6e000 r--s 00000000 08:02 4262184    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b4d6e000-b527c000 r--p 00000000 08:02 11014878   /usr/share/icons/hicolor/icon-theme.cache
b527c000-b63dd000 r--p 00000000 08:02 11293072   /usr/share/icons/crystalsvg/icon-theme.cache
b63dd000-b6a86000 r--p 00000000 08:02 11014882   /usr/share/icons/gnome/icon-theme.cache
b6a86000-b6cdd000 r--p 00000000 08:02 11013173   /usr/share/icons/Tango/icon-theme.cache
b6cdd000-b6cf9000 r-xp 00000000 08:02 10698767   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6cf9000-b6cfa000 rw-p 0001b000 08:02 10698767   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6cfa000-b6d5a000 rw-s 00000000 00:08 98305      /SYSV00000000 (deleted)
b6d5a000-b6dc7000 rw-p b6d5a000 00:00 0 
b6dc7000-b6dce000 r-xp 00000000 08:02 10634941   /usr/lib/libfam.so.0.0.0
b6dce000-b6dcf000 rw-p 00006000 08:02 10634941   /usr/lib/libfam.so.0.0.0
b6dcf000-b6dd5000 r-xp 00000000 08:02 2932763    /lib/libacl.so.1.1.0
b6dd5000-b6dd6000 rw-p 00005000 08:02 2932763    /lib/libacl.so.1.1.0
b6dd6000-b6dd9000 r-xp 00000000 08:02 2932767    /lib/libattr.so.1.1.0
b6dd9000-b6dda000 rw-p 00002000 08:02 2932767    /lib/libattr.so.1.1.0
b6dda000-b6ddc000 r--s 00000000 08:02 4262101    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6ddc000-b6ddf000 r--s 00000000 08:02 4262064    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6ddf000-b6de1000 r--s 00000000 08:02 4259944    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6de1000-b6de3000 r--s 00000000 08:02 4261577    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6de3000-b6de7000 r-xp 00000000 08:02 10698802   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6de7000-b6de8000 rw-p 00003000 08:02 10698802   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6de9000-b6df5000 r-xp 00000000 08:02 10637279   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6df5000-b6df6000 rw-p 0000b000 08:02 10637279   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6df6000-b6df7000 r-xp 00000000 08:02 10636868   /usr/lib/gconv/ISO8859-1.so
b6df7000-b6df9000 rw-p 00000000 08:02 10636868   /usr/lib/gconv/ISO8859-1.so
b6df9000-b6e34000 r--p 00000000 08:02 10699773   /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e34000-b6e35000 r--p 00000000 08:02 10699778   /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6e35000-b6e36000 r--p 00000000 08:02 10699781   /usr/lib/locale/en_US.utf8/LC_TIME
b6e36000-b6f0d000 r--p 00000000 08:02 10699772   /usr/lib/locale/en_US.utf8/LC_COLLATE
b6f0d000-b6f16000 r-xp 00000000 08:02 2936053    /lib/tls/i686/cmov/libnss_files-2.5.so
b6f16000-b6f18000 rw-p 00008000 08:02 2936053    /lib/tls/i686/cmov/libnss_files-2.5.so
b6f18000-b6f20000 r-xp 00000000 08:02 2936057    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f20000-b6f22000 rw-p 00007000 08:02 2936057    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f22000-b6f29000 r-xp 00000000 08:02 2936049    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f29000-b6f2b000 rw-p 00006000 08:02 2936049    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f2b000-b6f2e000 rw-p b6f2b000 00:00 0 
b6f2e000-b6f64000 r-xp 00000000 08:02 2932854    /lib/libsepol.so.1
b6f64000-b6f65000 rw-p 00035000 08:02 2932854    /lib/libsepol.so.1
b6f65000-b6f6f000 rw-p b6f65000 00:00 0 
b6f6f000-b6f72000 r-xp 00000000 08:02 10635094   /usr/lib/libgpg-error.so.0.3.0
b6f72000-b6f73000 rw-p 00002000 08:02 10635094   /usr/lib/libgpg-error.so.0.3.0
b6f73000-b6fc2000 r-xp 00000000 08:02 10634982   /usr/lib/libgcrypt.so.11.2.2
b6fc2000-b6fc4000 rw-p 0004e000 08:02 10634982   /usr/lib/libgcrypt.so.11.2.2
b6fc4000-b6fc5000 rw-p b6fc4000 00:00 0 
b6fc5000-b6fd9000 r-xp 00000000 08:02 10635438   /usr/lib/libtasn1.so.3.0.6
b6fd9000-b6fda000 rw-p 00013000 08:02 10635438   /usr/lib/libtasn1.so.3.0.6
b6fda000-b6fdc000 r-xp 00000000 08:02 2936070    /lib/tls/i686/cmov/libutil-2.5.so
b6fdc000-b6fde000 rw-p 00001000 08:02 2936070    /lib/tls/i686/cmov/libutil-2.5.so
b6fde000-b6ff2000 r-xp 00000000 08:02 2932853    /lib/libselinux.so.1
b6ff2000-b6ff4000 rw-p 00013000 08:02 2932853    /lib/libselinux.so.1
b6ff4000-b7003000 r-xp 00000000 08:02 2936064    /lib/tls/i686/cmov/libresolv-2.5.so
b7003000-b7005000 rw-p 0000f000 08:02 2936064    /lib/tls/i686/cmov/libresolv-2.5.so
b7005000-b7007000 rw-p b7005000 00:00 0 
b7007000-b7015000 r-xp 00000000 08:02 10634820   /usr/lib/libavahi-client.so.3.2.2
b7015000-b7016000 rw-p 0000e000 08:02 10634820   /usr/lib/libavahi-client.so.3.2.2
b7016000-b7017000 rw-p b7016000 00:00 0 
b7017000-b7021000 r-xp 00000000 08:02 10634822   /usr/lib/libavahi-common.so.3.4.3
b7021000-b7022000 rw-p 00009000 08:02 10634822   /usr/lib/libavahi-common.so.3.4.3
b7022000-b7024000 r-xp 00000000 08:02 10634826   /usr/lib/libavahi-glib.so.1.0.1
b7024000-b7025000 rw-p 00001000 08:02 10634826   /usr/lib/libavahi-glib.so.1.0.1
b7025000-b708f000 r-xp 00000000 08:02 10635090   /usr/lib/libgnutls.so.13.0.9
b708f000-b7095000 rw-p 0006a000 08:02 10635090   /usr/lib/libgnutls.so.13.0.9
b7095000-b70b7000 r-xp 00000000 08:02 10635014   /usr/lib/libpng12.so.0.15.0
b70b7000-b70b8000 rw-p 00021000 08:02 10635014   /usr/lib/libpng12.so.0.15.0
b70b8000-b70d6000 r-xp 00000000 08:02 10634937   /usr/lib/libexpat.so.1.0.0
b70d6000-b70d8000 rw-p 0001d000 08:02 10634937   /usr/lib/libexpat.so.1.0.0
b70d8000-b70d9000 rw-p b70d8000 00:00 0 
b70d9000-b7141000 r-xp 00000000 08:02 10634869   /usr/lib/libfreetype.so.6.3.10
b7141000-b7144000 rw-p 00068000 08:02 10634869   /usr/lib/libfreetype.so.6.3.10
b7144000-b7157000 r-xp 00000000 08:02 10635496   /usr/lib/libz.so.1.2.3
b7157000-b7158000 rw-p 00012000 08:02 10635496   /usr/lib/libz.so.1.2.3
b7158000-b716b000 r-xp 00000000 08:02 2936047    /lib/tls/i686/cmov/libnsl-2.5.so
b716b000-b716d000 rw-p 00012000 08:02 2936047    /lib/tls/i686/cmov/libnsl-2.5.so
b716d000-b716f000 rw-p b716d000 00:00 0 
b716f000-b7173000 r-xp 00000000 08:02 10634727   /usr/lib/libORBitCosNaming-2.so.0.1.0
b7173000-b7174000 rw-p 00003000 08:02 10634727   /usr/lib/libORBitCosNaming-2.so.0.1.0
b7174000-b7175000 rw-p b7174000 00:00 0 
b7175000-b7179000 r-xp 00000000 08:02 10634752   /usr/lib/libXdmcp.so.6.0.0
b7179000-b717a000 rw-p 00003000 08:02 10634752   /usr/lib/libXdmcp.so.6.0.0
b717a000-b7198000 r-xp 00000000 08:02 10635219   /usr/lib/libjpeg.so.62.0.0
b7198000-b7199000 rw-p 0001d000 08:02 10635219   /usr/lib/libjpeg.so.62.0.0
b7199000-b71a1000 r-xp 00000000 08:02 10635428   /usr/lib/libstartup-notification-1.so.0.0.0
b71a1000-b71a2000 rw-p 00007000 08:02 10635428   /usr/lib/libstartup-notification-1.so.0.0.0
b71a2000-b71a3000 rw-p b71a2000 00:00 0 
b71a3000-b71aa000 r-xp 00000000 08:02 2936066    /lib/tls/i686/cmov/librt-2.5.so
b71aa000-b71ac000 rw-p 00006000 08:02 2936066    /lib/tls/i686/cmov/librt-2.5.so
b71ac000-b71b0000 r-xp 00000000 08:02 10635146   /usr/lib/libgthread-2.0.so.0.1200.11
b71b0000-b71b1000 rw-p 00003000 08:02 10635146   /usr/lib/libgthread-2.0.so.0.1200.11
b71b1000-b71b3000 r-xp 00000000 08:02 2936042    /lib/tls/i686/cmov/libdl-2.5.so
b71b3000-b71b5000 rw-p 00001000 08:02 2936042    /lib/tls/i686/cmov/libdl-2.5.so
b71b5000-b71b7000 r-xp 00000000 08:02 10635048   /usr/lib/libgmodule-2.0.so.0.1200.11
b71b7000-b71b8000 rw-p 00002000 08:02 10635048   /usr/lib/libgmodule-2.0.so.0.1200.11
b71b8000-b720e000 r-xp 00000000 08:02 10635082   /usr/lib/libgnomevfs-2.so.0.1800.1
b720e000-b7211000 rw-p 00055000 08:02 10635082   /usr/lib/libgnomevfs-2.so.0.1800.1
b7211000-b727f000 r-xp 00000000 08:02 10634845   /usr/lib/libcairo.so.2.11.1
b727f000-b7281000 rw-p 0006d000 08:02 10634845   /usr/lib/libcairo.so.2.11.1
b7281000-b7282000 rw-p b7281000 00:00 0 
b7282000-b7286000 r-xp 00000000 08:02 10634758   /usr/lib/libXfixes.so.3.1.0
b7286000-b7287000 rw-p 00003000 08:02 10634758   /usr/lib/libXfixes.so.3.1.0
b7287000-b728f000 r-xp 00000000 08:02 10634748   /usr/lib/libXcursor.so.1.0.2
b728f000-b7290000 rw-p 00007000 08:02 10634748   /usr/lib/libXcursor.so.1.0.2
b7290000-b7297000 r-xp 00000000 08:02 10634764   /usr/lib/libXi.so.6.0.0
b7297000-b7298000 rw-p 00006000 08:02 10634764   /usr/lib/libXi.so.6.0.0
b7298000-b729a000 r-xp 00000000 08:02 10634766   /usr/lib/libXinerama.so.1.0.0
b729a000-b729b000 rw-p 00001000 08:02 10634766   /usr/lib/libXinerama.so.1.0.0
b729b000-b72a2000 r-xp 00000000 08:02 10634778   /usr/lib/libXrender.so.1.3.0
b72a2000-b72a3000 rw-p 00006000 08:02 10634778   /usr/lib/libXrender.so.1.3.0
b72a3000-b72b0000 r-xp 00000000 08:02 10634756   /usr/lib/libXext.so.6.4.0
b72b0000-b72b1000 rw-p 0000d000 08:02 10634756   /usr/lib/libXext.so.6.4.0
b72b1000-b72b2000 rw-p b72b1000 00:00 0 
b72b2000-b72d5000 r-xp 00000000 08:02 10634943   /usr/lib/libfontconfig.so.1.2.0
b72d5000-b72dd000 rw-p 00023000 08:02 10634943   /usr/lib/libfontconfig.so.1.2.0
b72dd000-b72e4000 r-xp 00000000 08:02 10635327   /usr/lib/libpangocairo-1.0.so.0.1600.2
b72e4000-b72e5000 rw-p 00007000 08:02 10635327   /usr/lib/libpangocairo-1.0.so.0.1600.2
b72e5000-b730f000 r-xp 00000000 08:02 10635329   /usr/lib/libpangoft2-1.0.so.0.1600.2
b730f000-b7310000 rw-p 0002a000 08:02 10635329   /usr/lib/libpangoft2-1.0.so.0.1600.2
b7310000-b7324000 r-xp 00000000 08:02 10634804   /usr/lib/libart_lgpl_2.so.2.3.17
b7324000-b7325000 rw-p 00013000 08:02 10634804   /usr/lib/libart_lgpl_2.so.2.3.17
b7325000-b732c000 r-xp 00000000 08:02 2932843    /lib/libpopt.so.0.0.0
b732c000-b732d000 rw-p 00006000 08:02 2932843    /lib/libpopt.so.0.0.0
b732d000-b7356000 r-xp 00000000 08:02 10635064   /usr/lib/libgnomecanvas-2.so.0.1400.0
b7356000-b7357000 rw-p 00029000 08:02 10635064   /usr/lib/libgnomecanvas-2.so.0.1400.0
b7357000-b7358000 rw-p b7357000 00:00 0 
b7358000-b73b3000 r-xp 00000000 08:02 10634841   /usr/lib/libbonoboui-2.so.0.0.0
b73b3000-b73b6000 rw-p 0005a000 08:02 10634841   /usr/lib/libbonoboui-2.so.0.0.0
b73b6000-b74cd000 r-xp 00000000 08:02 10635490   /usr/lib/libxml2.so.2.6.27
b74cd000-b74d3000 rw-p 00116000 08:02 10635490   /usr/lib/libxml2.so.2.6.27
b74d3000-b7593000 r-xp 00000000 08:02 10634806   /usr/lib/libasound.so.2.0.0
b7593000-b7598000 rw-p 000bf000 08:02 10634806   /usr/lib/libasound.so.2.0.0
b7598000-b75bd000 r-xp 00000000 08:02 2936044    /lib/tls/i686/cmov/libm-2.5.so
b75bd000-b75bf000 rw-p 00024000 08:02 2936044    /lib/tls/i686/cmov/libm-2.5.so
b75bf000-b75df000 r-xp 00000000 08:02 10634818   /usr/lib/libaudiofile.so.0.0.2
b75df000-b75e1000 rw-p 00020000 08:02 10634818   /usr/lib/libaudiofile.so.0.0.2
b75e1000-b771c000 r-xp 00000000 08:02 2936036    /lib/tls/i686/cmov/libc-2.5.so
b771c000-b771d000 r--p 0013b000 08:02 2936036    /lib/tls/i686/cmov/libc-2.5.so
b771d000-b771f000 rw-p 0013c000 08:02 2936036    /lib/tls/i686/cmov/libc-2.5.so
b771f000-b7723000 rw-p b771f000 00:00 0 
b7723000-b772a000 r-xp 00000000 08:02 2932874    /lib/libwrap.so.0.7.6
b772a000-b772b000 rw-p 00007000 08:02 2932874    /lib/libwrap.so.0.7.6
b772b000-b77bf000 r-xp 00000000 08:02 10635038   /usr/lib/libglib-2.0.so.0.1200.11
b77bf000-b77c0000 rw-p 00093000 08:02 10635038   /usr/lib/libglib-2.0.so.0.1200.11
b77c0000-b77cc000 r-xp 00000000 08:02 10635054   /usr/lib/libgnome-keyring.so.0.0.1
b77cc000-b77cd000 rw-p 0000b000 08:02 10635054   /usr/lib/libgnome-keyring.so.0.0.1
b77cd000-b7806000 r-xp 00000000 08:02 10635092   /usr/lib/libgobject-2.0.so.0.1200.11
b7806000-b7807000 rw-p 00039000 08:02 10635092   /usr/lib/libgobject-2.0.so.0.1200.11
b7807000-b7838000 r-xp 00000000 08:02 10634879   /usr/lib/libdbus-1.so.3.2.0
b7838000-b7839000 rw-p 00031000 08:02 10634879   /usr/lib/libdbus-1.so.3.2.0
b7839000-b7853000 r-xp 00000000 08:02 10634881   /usr/lib/libdbus-glib-1.so.2.1.0
b7853000-b7854000 rw-p 0001a000 08:02 10634881   /usr/lib/libdbus-glib-1.so.2.1.0
b7854000-b7855000 rw-p b7854000 00:00 0 
b7855000-b7868000 r-xp 00000000 08:02 2936062    /lib/tls/i686/cmov/libpthread-2.5.so
b7868000-b786a000 rw-p 00013000 08:02 2936062    /lib/tls/i686/cmov/libpthread-2.5.so
b786a000-b786c000 rw-p b786a000 00:00 0 
b786c000-b78b5000 r-xp 00000000 08:02 10634723   /usr/lib/libORBit-2.so.0.1.0
b78b5000-b78bf000 rw-p 00048000 08:02 10634723   /usr/lib/libORBit-2.so.0.1.0
b78bf000-b78ee000 r-xp 00000000 08:02 10634980   /usr/lib/libgconf-2.so.4.1.2
b78ee000-b78f1000 rw-p 0002e000 08:02 10634980   /usr/lib/libgconf-2.so.4.1.2
b78f1000-b7904000 r-xp 00000000 08:02 10634839   /usr/lib/libbonobo-activation.so.4.0.0
b7904000-b7906000 rw-p 00013000 08:02 10634839   /usr/lib/libbonobo-activation.so.4.0.0
b7906000-b7958000 r-xp 00000000 08:02 10634837   /usr/lib/libbonobo-2.so.0.0.0
b7958000-b7962000 rw-p 00051000 08:02 10634837   /usr/lib/libbonobo-2.so.0.0.0
b7962000-b7963000 rw-p b7962000 00:00 0 
b7963000-b7a50000 r-xp 00000000 08:02 10634735   /usr/lib/libX11.so.6.2.0
b7a50000-b7a54000 rw-p 000ed000 08:02 10634735   /usr/lib/libX11.so.6.2.0
b7a54000-b7a90000 r-xp 00000000 08:02 10635325   /usr/lib/libpango-1.0.so.0.1600.2
b7a90000-b7a92000 rw-p 0003b000 08:02 10635325   /usr/lib/libpango-1.0.so.0.1600.2
b7a92000-b7a97000 r-xp 00000000 08:02 10634776   /usr/lib/libXrandr.so.2.1.0
b7a97000-b7a98000 rw-p 00005000 08:02 10634776   /usr/lib/libXrandr.so.2.1.0
b7a98000-b7aae000 r-xp 00000000 08:02 10635002   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7aae000-b7aaf000 rw-p 00015000 08:02 10635002   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7aaf000-b7ac8000 r-xp 00000000 08:02 10634812   /usr/lib/libatk-1.0.so.0.1809.1
b7ac8000-b7aca000 rw-p 00018000 08:02 10634812   /usr/lib/libatk-1.0.so.0.1809.1
b7aca000-b7b4d000 r-xp 00000000 08:02 10635000   /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b4d000-b7b50000 rw-p 00083000 08:02 10635000   /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b50000-b7b51000 rw-p b7b50000 00:00 0 
b7b51000-b7ea2000 r-xp 00000000 08:02 10635149   /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ea2000-b7ea8000 rw-p 00351000 08:02 10635149   /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ea8000-b7ea9000 rw-p b7ea8000 00:00 0 
b7ea9000-b7ebd000 r-xp 00000000 08:02 10635050   /usr/lib/libgnome-2.so.0.1800.0
b7ebd000-b7ebe000 rw-p 00014000 08:02 10635050   /usr/lib/libgnome-2.so.0.1800.0
b7ebe000-b7ed3000 r-xp 00000000 08:02 10634713   /usr/lib/libICE.so.6.3.0
b7ed3000-b7ed5000 rw-p 00014000 08:02 10634713   /usr/lib/libICE.so.6.3.0
b7ed5000-b7ed6000 rw-p b7ed5000 00:00 0 
b7ed6000-b7ede000 r-xp 00000000 08:02 10634731   /usr/lib/libSM.so.6.0.0
b7ede000-b7edf000 rw-p 00007000 08:02 10634731   /usr/lib/libSM.so.6.0.0
b7edf000-b7f69000 r-xp 00000000 08:02 10635080   /usr/lib/libgnomeui-2.so.0.1788.4
b7f69000-b7f6d000 rw-p 00089000 08:02 10635080   /usr/lib/libgnomeui-2.so.0.1788.4
b7f6d000-b7f81000 r-xp 00000000 08:02 10635052   /usr/lib/libgnome-desktop-2.so.2.3.5
b7f81000-b7f82000 rw-p 00014000 08:02 10635052   /usr/lib/libgnome-desktop-2.so.2.3.5
b7f82000-b7f83000 rw-p b7f82000 00:00 0 
b7f83000-b7f8c000 r-xp 00000000 08:02 10634928   /usr/lib/libesd.so.0.2.36
b7f8c000-b7f8d000 rw-p 00009000 08:02 10634928   /usr/lib/libesd.so.0.2.36
b7f8d000-b7f8f000 r-xp 00000000 08:02 10634741   /usr/lib/libXau.so.6.0.0
b7f8f000-b7f90000 rw-p 00001000 08:02 10634741   /usr/lib/libXau.so.6.0.0
b7f90000-b7f91000 r--p 00000000 08:02 10699776   /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f91000-b7f92000 r--p 00000000 08:02 10699782   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f92000-b7f93000 r--p 00000000 08:02 10699779   /usr/lib/locale/en_US.utf8/LC_PAPER
b7f93000-b7f94000 r--p 00000000 08:02 10699777   /usr/lib/locale/en_US.utf8/LC_NAME
b7f94000-b7f95000 r--p 00000000 08:02 10699771   /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f95000-b7f96000 r--p 00000000 08:02 10699780   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f96000-b7f97000 r--p 00000000 08:02 10699775   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f97000-b7f9e000 r--s 00000000 08:02 10636921   /usr/lib/gconv/gconv-modules.cache
b7f9e000-b7f9f000 r--p 00000000 08:02 10699774   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f9f000-b7fa1000 rw-p b7f9f000 00:00 0 
b7fa1000-b7fba000 r-xp 00000000 08:02 2932757    /lib/ld-2.5.so
b7fba000-b7fbc000 rw-p 00019000 08:02 2932757    /lib/ld-2.5.so
bf7fc000-bf811000 rw-p bf7fc000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
seahorse nautilus module initialized

(evolution-alarm-notify:5964): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

---

### Post by hwshadow on 2007-08-08
is there any way to make a package of ever component ive download like all the app and stuff i have downloaded so on reinstall if i have to i pop the the package into terminal and it fetchs and install all that again i know the synaptic package manager does something like that but it i its all mixed : the original stuff from the live cd and the new packages i have downloaded and installed.

---

### Post by apetresc on 2007-08-08
> **hwshadow said:**
> is there any way to make a package of ever component ive download like all the app and stuff i have downloaded so on reinstall if i have to i pop the the package into terminal and it fetchs and install all that again i know the synaptic package manager does something like that but it i its all mixed : the original stuff from the live cd and the new packages i have downloaded and installed.

Sure :) ```
dpkg -l | awk '{print $2}'
```That'll give you a list of every package currently installed on your system (except for the first two lines, those are junk, get rid of them manually). Then when you reinstall you can just feed that list back into apt.

---

### Post by musee-urrah on 2007-08-08
Did you change the splash screen? The one that shows after you login?

This happened to me for a while - and I figured that if the splash screen isn't wide enough, ubuntu only loads some of the programs and it messes up.

It seems to be the case, though I'm not sure myself. Anyways, try changing your splash screen image to something wider...or to the default. Instructions:

1. Open the terminal and run "gconf-editor". (Or go to Applications > System Tools > Configuration Editor, if it's there.)
2. In the little navigation area on the right, go to apps > gnome-session.
3. There's a splash_image value with the splash image that's currently being used. Try changing it to "splash/ubuntu-splash.png" - which usually is the default unless you changed the link by yourself...

Restart your computer and it'll work - that is, if I think I know what the problem is. xD
ja mata.

~musee

---

### Post by apetresc on 2007-08-08
> **musee-urrah said:**
> Did you change the splash screen? The one that shows after you login?

This happened to me for a while - and I figured that if the splash screen isn't wide enough, ubuntu only loads some of the programs and it messes up.
Err. I've never looked at the source for gnome-splashscreen-manager, but I'm 99.9999999% sure this is not an issue.

---

### Post by hwshadow on 2007-08-22
ya i did lol i try that that may be it cause its like 600 x 150 thx ill try it tomorrow i was on vacation.  
thanks in advance.

---

### Post by hwshadow on 2007-08-23
YEAH YOU GUYS AMAZING 
3 cheers:
hip hip hurray! :lolflag:
hip hip hurray! :lolflag:
hip hip hurray! :lolflag:
hip hip hurray! :lolflag:
woopppps that was 4 oh well you guys deserve it :D 


[SIZE="7"]CASE CLOSED[/SIZE]

P.S. I can believe that generated the huge error list above, but live and learn i guess

---

