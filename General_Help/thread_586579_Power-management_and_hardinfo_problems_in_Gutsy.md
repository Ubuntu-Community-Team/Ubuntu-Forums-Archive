---
title: "Power-management and hardinfo problems in Gutsy?"
date: 2007-10-22
forum: General Help
---

### Post by chunchengch on 2007-10-22
I asked for help to extend the battery life in my another thread [http://ubuntuforums.org/showthread.php?p=3599516#post3599516](http://ubuntuforums.org/showthread.php?p=3599516#post3599516), but when I find different informations from the power-management and package hardinfo (installed from Synaptic) for the same battery, I think I have to start a new thread for further assistance.

1. The power-management shows the same message "the battery is fully charged and provides 1 hour and 55 minutes battery runtime". however, I check the battery information with hardinfo, the battery is charged only 86.63%. I wonder which information is correct?

[ATTACH]47296[/ATTACH]

2. Every time I activate the hardinfo, just 5 seconds later, it will close itself automatically, what is the problem? and how can I fix it?


Thanks for any help!

---

### Post by kranz on 2007-10-22
I have same problem. And not only on one computer - I have 32bit laptop and 64bit desktop. And both have same problem. Starting hardinfo from terminal give up this:

*** glibc detected *** hardinfo: munmap_chunk(): invalid pointer: 0x000000000092ef60 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2aec4eecd826]
/usr/lib/libglib-2.0.so.0(g_hash_table_insert+0xa0)[0x2aec4dd411b0]
hardinfo[0x40b5e1]
hardinfo[0x40be4c]
/usr/lib/libglib-2.0.so.0[0x2aec4dd4d70b]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1c3)[0x2aec4dd4cfd3]
/usr/lib/libglib-2.0.so.0[0x2aec4dd502dd]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0x2aec4dd505ea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x2aec4ae98883]
hardinfo(main+0x107)[0x40a167]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2aec4ee75b44]
hardinfo[0x409fc9]
======= Memory map: ========
00400000-00420000 r-xp 00000000 03:02 1720592                            /usr/bin/hardinfo
00620000-00622000 rw-p 00020000 03:02 1720592                            /usr/bin/hardinfo
00622000-00982000 rw-p 00622000 00:00 0                                  [heap]
2aec4ab24000-2aec4ab41000 r-xp 00000000 03:02 669139                     /lib/ld-2.6.1.so
2aec4ab41000-2aec4ab44000 rw-p 2aec4ab41000 00:00 0 
2aec4ab44000-2aec4ab45000 r--p 00000000 03:02 1849133                    /usr/lib/locale/et_EE.utf8/LC_IDENTIFICATION
2aec4ab45000-2aec4ab4c000 r--s 00000000 03:02 1717543                    /usr/lib/gconv/gconv-modules.cache
2aec4ab4c000-2aec4ab4d000 r--p 00000000 03:02 1779534                    /usr/lib/locale/et_EE.utf8/LC_MEASUREMENT
2aec4ab4d000-2aec4ab4e000 r--p 00000000 03:02 1849132                    /usr/lib/locale/et_EE.utf8/LC_TELEPHONE
2aec4ab4e000-2aec4ab4f000 r--p 00000000 03:02 1849131                    /usr/lib/locale/et_EE.utf8/LC_ADDRESS
2aec4ab4f000-2aec4ab50000 r--p 00000000 03:02 1779536                    /usr/lib/locale/et_EE.utf8/LC_NAME
2aec4ab50000-2aec4ab51000 r--p 00000000 03:02 1779538                    /usr/lib/locale/et_EE.utf8/LC_PAPER
2aec4ab51000-2aec4ab52000 r--p 00000000 03:02 1849130                    /usr/lib/locale/et_EE.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2aec4ab52000-2aec4ab53000 r--p 00000000 03:02 1849128                    /usr/lib/locale/et_EE.utf8/LC_MONETARY
2aec4ab53000-2aec4ac33000 r--p 00000000 03:02 1849127                    /usr/lib/locale/et_EE.utf8/LC_COLLATE
2aec4ac33000-2aec4ac34000 r--p 00000000 03:02 1849126                    /usr/lib/locale/et_EE.utf8/LC_TIME
2aec4ac34000-2aec4ac35000 r--p 00000000 03:02 1849125                    /usr/lib/locale/et_EE.utf8/LC_NUMERIC
2aec4ac35000-2aec4ac74000 r--p 00000000 03:02 1779532                    /usr/lib/locale/et_EE.utf8/LC_CTYPE
2aec4ac74000-2aec4ac83000 r--p 00000000 03:02 67460                      /usr/share/locale-langpack/et/LC_MESSAGES/gtk20.mo
2aec4ac83000-2aec4ac91000 r--p 00000000 03:02 67461                      /usr/share/locale-langpack/et/LC_MESSAGES/gtk20-properties.mo
2aec4ad40000-2aec4ad42000 rw-p 0001c000 03:02 669139                     /lib/ld-2.6.1.so
2aec4ad42000-2aec4b113000 r-xp 00000000 03:02 1715611                    /usr/lib/libgtk-x11-2.0.so.0.1200.0
2aec4b113000-2aec4b312000 ---p 003d1000 03:02 1715611                    /usr/lib/libgtk-x11-2.0.so.0.1200.0
2aec4b312000-2aec4b31e000 rw-p 003d0000 03:02 1715611                    /usr/lib/libgtk-x11-2.0.so.0.1200.0
2aec4b31e000-2aec4b320000 rw-p 2aec4b31e000 00:00 0 
2aec4b320000-2aec4b3b9000 r-xp 00000000 03:02 1715456                    /usr/lib/libgdk-x11-2.0.so.0.1200.0
2aec4b3b9000-2aec4b5b9000 ---p 00099000 03:02 1715456                    /usr/lib/libgdk-x11-2.0.so.0.1200.0
2aec4b5b9000-2aec4b5be000 rw-p 00099000 03:02 1715456                    /usr/lib/libgdk-x11-2.0.so.0.1200.0
2aec4b5be000-2aec4b5dc000 r-xp 00000000 03:02 1715275                    /usr/lib/libatk-1.0.so.0.2009.1
2aec4b5dc000-2aec4b7dc000 ---p 0001e000 03:02 1715275                    /usr/lib/libatk-1.0.so.0.2009.1
2aec4b7dc000-2aec4b7df000 rw-p 0001e000 03:02 1715275                    /usr/lib/libatk-1.0.so.0.2009.1
2aec4b7df000-2aec4b7f8000 r-xp 00000000 03:02 1715458                    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2aec4b7f8000-2aAborted (core dumped)

---

### Post by LavianoTS386 on 2007-11-15
I too am having the same problems on both my desktop and my laptop (nForce & AMD), but on another intel machine it runs fine.

---

