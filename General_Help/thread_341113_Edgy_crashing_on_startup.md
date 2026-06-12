---
title: "Edgy crashing on startup"
date: 2007-01-18
forum: General Help
---

### Post by Sohum on 2007-01-18
Edgy boots. 
I log in to my account.
It starts up; programs start. 
At some point in the sequence, Edgy crashes. 
The clock stops ticking, the system monitor applet stops moving. 
I can move the mouse on top of the screen, but nothing responds. It's as if I'm moving it on a bitmap.

It's not a problem with Edgy, as I have another account on the machine, which starts up fine and is usable.

I think a program is crashing on startup.

Any logs I could check to figure out the problem?
How do you edit the startup programs of an account from the command line?

---

### Post by mcduck on 2007-01-18
> **Sohum said:**
> 
Any logs I could check to figure out the problem?

try ~/.xsession-errors

---

### Post by Sohum on 2007-01-18
Right. Here it is. I couldn't make much sense of it.
Does the end mean that beagle is crashing?

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sohum"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/desktop:/tmp/.ICE-unix/5700
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
python: can't open file '/media/common/sohum/todo/JabberBot/todo_jbot.py': [Errno 2] No such file or directory

(process:5889): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
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
evolution-alarm-notify-Message: Setting timeout for 40879 1169164800 1169123921
evolution-alarm-notify-Message:  Fri Jan 19 10:00:00 2007

evolution-alarm-notify-Message:  Thu Jan 18 22:38:41 2007

DCOPClient::attachInternal. Attach failed Could not open network socket
Traceback (most recent call last):
  File "/usr/bin/specto", line 38, in ?
    specto = Specto()
  File "/usr/lib/python2.4/site-packages/specto/main.py", line 85, in __init__
    watch_value_db = self.watch_io.read_options() 
  File "/usr/lib/python2.4/site-packages/specto/watch.py", line 176, in read_options
    values['type'] = int(watch_options['type'])
KeyError: 'type'
DCOPClient::attachInternal. Attach failed Could not open network socket
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
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
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
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
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
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
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
kbuildsycoca running...
DCOPClient::attachInternal. Attach failed Could not open network socket
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
*** glibc detected *** beryl: double free or corruption (fasttop): 0x0818a6d8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c538bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7c53a44]
/usr/lib/libX11.so.6(XFree+0x1d)[0xb7b5df6d]
/usr/lib/beryl/libthumbnail.so[0xb441a59d]
/usr/lib/beryl/libthumbnail.so[0xb441b4ac]
/usr/lib/beryl/libswitcher.so[0xb440c8a7]
/usr/lib/beryl/libwater.so[0xb43ffc98]
/usr/lib/beryl/libwobbly.so[0xb43f9a50]
/usr/lib/beryl/libscale.so[0xb442597e]
/usr/lib/beryl/librotate.so[0xb442ef16]
beryl(eventLoop+0x145)[0x8057a15]
beryl(main+0x502)[0x80513b2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7c028cc]
beryl[0x8050d51]
======= Memory map: ========
08048000-0807a000 r-xp 00000000 08:02 2166031    /usr/bin/beryl
0807a000-0807b000 rw-p 00031000 08:02 2166031    /usr/bin/beryl
0807b000-083ba000 rw-p 0807b000 00:00 0          [heap]
b1077000-b1078000 rw-s 00000000 00:08 4292642    /SYSV00000000 (deleted)
b10a6000-b1126000 rw-s 34fed000 00:0d 10103      /dev/nvidia0
b1126000-b17b9000 rw-p b1126000 00:00 0 
b19b9000-b210d000 rw-p b19b9000 00:00 0 
b230d000-b2a61000 rw-p b230d000 00:00 0 
b2d5e000-b2d5f000 rw-s 00000000 00:08 4194335    /SYSV00000000 (deleted)
b2d5f000-b2d60000 rw-s 00000000 00:08 4161566    /SYSV00000000 (deleted)
b3489000-b3925000 rw-p b3489000 00:00 0 
b39c4000-b3ac4000 rw-p b39c4000 00:00 0 
b3c3f000-b3c40000 rw-s 00000000 00:08 4358180    /SYSV00000000 (deleted)
b4000000-b4021000 rw-p b4000000 00:00 0 
b4021000-b4100000 ---p b4021000 00:00 0 
b4106000-b41b3000 rw-p b4106000 00:00 0 
b41b8000-b41e4000 rw-p b41b8000 00:00 0 
b41e4000-b41e5000 rw-s 00000000 00:08 4489254    /SYSV00000000 (deleted)
b41e6000-b41e7000 rw-s 00000000 00:08 4423713    /SYSV00000000 (deleted)
b41e7000-b41e8000 rw-s 00000000 00:08 4128797    /SYSV00000000 (deleted)
b4232000-b4233000 rw-s 00000000 00:08 3997721    /SYSV00000000 (deleted)
b4233000-b4234000 rw-s 00000000 00:08 3964952    /SYSV00000000 (deleted)
b4234000-b4235000 rw-s 00000000 00:08 3932183    /SYSV00000000 (deleted)
b4235000-b4236000 rw-s 00000000 00:08 3899414    /SYSV00000000 (deleted)
b4236000-b4237000 rw-s 00000000 00:08 3866645    /SYSV00000000 (deleted)
b423c000-b4246000 r-xp 00000000 08:02 1818691    /lib/libgcc_s.so.1
b4246000-b4247000 rw-p 00009000 08:02 1818691    /lib/libgcc_s.so.1
b4258000-b4259000 rw-s 00000000 00:08 4456485    /SYSV00000000 (deleted)
b4259000-b425a000 rw-s 00000000 00:08 4685867    /SYSV00000000 (deleted)
b425a000-b425b000 rw-s 00000000 00:08 4653098    /SYSV00000000 (deleted)
b425b000-b425c000 rw-s 00000000 00:08 4620329    /SYSV00000000 (deleted)
b425c000-b425d000 rw-s 00000000 00:08 3833876    /SYSV00000000 (deleted)
b425d000-b425e000 rw-s 00000000 00:08 3801107    /SYSV00000000 (deleted)
b425e000-b43ea000 rw-p b425e000 00:00 0 
b43ea000-b43eb000 rw-s 00000000 00:08 3637262    /SYSV00000000 (deleted)
b43eb000-b43ec000 rw-s 00000000 00:08 3604493    /SYSV00000000 (deleted)
b43ec000-b43f2000 r-xp 00000000 08:02 2167501    /usr/lib/beryl/libtile.so
b43f2000-b43f3000 rw-p 00006000 08:02 2167501    /usr/lib/beryl/libtile.so
b43f3000-b43fb000 r-xp 00000000 08:02 2167497    /usr/lib/beryl/libwobbly.so
b43fb000-b43fc000 rw-p 00008000 08:02 2167497    /usr/lib/beryl/libwobbly.so
b43fc000-b4403000 r-xp 00000000 08:02 2167496    /usr/lib/beryl/libwater.so
b4403000-b4404000 rw-p 00006000 08:02 2167496    /usr/lib/beryl/libwater.so
b4404000-b4406000 r-xp 00000000 08:02 2167472    /usr/lib/beryl/libsvg.so
b4406000-b4407000 rw-p 00001000 08:02 2167472    /usr/lib/beryl/libsvg.so
b4407000-b440e000 r-xp 00000000 08:02 2167493    /usr/lib/beryl/libswitcher.so
b440e000-b440f000 rw-p 00006000 08:02 2167493    /usr/lib/beryl/libswitcher.so
b440f000-b4413000 r-xp 00000000 08:02 2167469    /usr/lib/beryl/libsnow.so
b4413000-b4414000 rw-p 00003000 08:02 2167469    /usr/lib/beryl/libsnow.so
b4414000-b4418000 r-xp 00000000 08:02 2167470    /usr/lib/beryl/libsplash.so
b4418000-b4419000 rw-p 00003000 08:02 2167470    /usr/lib/beryl/libsplash.so
b4419000-b441d000 r-xp 00000000 08:02 2167494    /usr/lib/beryl/libthumbnail.so
b441d000-b441e000 rw-p 00003000 08:02 2167494    /usr/lib/beryl/libthumbnail.so
b441e000-b4427000 r-xp 00000000 08:02 2167465    /usr/lib/beryl/libscale.so
b4427000-b4428000 rw-p 00008000 08:02 2167465    /usr/lib/beryl/libscale.so
b4428000-b4431000 r-xp 00000000 08:02 2167464    /usr/lib/beryl/librotate.so
b4431000-b4432000 rw-p 00008000 08:02 2167464    /usr/lib/beryl/librotate.so
b4432000-b4438000 r-xp 00000000 08:02 2167462    /usr/lib/beryl/libput.so
b4438000-b4439000 rw-p 00005000 08:02 2167462    /usr/lib/beryl/libput.so
b4439000-b443b000 r-xp 00000000 08:02 2167461    /usr/lib/beryl/libpng.so
b443b000-b443c000 rw-p 00002000 08:02 2167461    /usr/lib/beryl/libpng.so
b443c000-b443f000 r-xp 00000000 08:02 2167459    /usr/lib/beryl/libplace.so
b443f000-b4440000 rw-p 00002000 08:02 2167459    /usr/lib/beryl/libplace.so
b4440000-b4458000 r-xp 00000000 08:02 2167454    /usr/lib/beryl/libgroup.so
b4458000-b4469000 rw-p 00018000 08:02 2167454    /usr/lib/beryl/libgroup.so
b4469000-b4478000 r-xp 00000000 08:02 1818665    /lib/libbz2.so.1.0.3
b4478000-b4479000 rw-p 0000f000 08:02 1818665    /lib/libbz2.so.1.0.3
b4479000-b4495000 r-xp 00000000 08:02 2164136    /usr/lib/libexpat.so.1.0.0
b4495000-b4497000 rw-p 0001c000 08:02 2164136    /usr/lib/libexpat.so.1.0.0
b4497000-b44cf000 r-xp 00000000 08:02 2164523    /usr/lib/libpango-1.0.so.0.1400.5
b44cf000-b44d1000 rw-p 00037000 08:02 2164523    /usr/lib/libpango-1.0.so.0.1400.5
b44d1000-b44d8000 r-xp 00000000 08:02 2164525    /usr/lib/libpangocairo-1.0.so.0.1400.5
b44d8000-b44d9000 rw-p 00006000 08:02 2164525    /usr/lib/libpangocairo-1.0.so.0.1400.5
b44d9000-b4503000 r-xp 00000000 08:02 2164527    /usr/lib/libpangoft2-1.0.so.0.1400.5
b4503000-b4504000 rw-p 00029000 08:02 2164527    /usr/lib/libpangoft2-1.0.so.0.1400.5
b4504000-b4617000 r-xp 00000000 08:02 2164670    /usr/lib/libxml2.so.2.6.26
b4617000-b461c000 rw-p 00113000 08:02 2164670    /usr/lib/libxml2.so.2.6.26
b461c000-b461d000 rw-p b461c000 00:00 0 
b461d000-b464d000 r-xp 00000000 08:02 2164063    /usr/lib/libcroco-0.6.so.3.0.1
b464d000-b4650000 rw-p 0002f000 08:02 2164063    /usr/lib/libcroco-0.6.so.3.0.1
b4650000-b467b000 r-xp 00000000 08:02 2163145    /usr/lib/libgsf-1.so.114.0.1
b467b000-b467e000 rw-p 0002a000 08:02 2163145    /usr/lib/libgsf-1.so.114.0.1
b467e000-b467f000 rw-p b467e000 00:00 0 
b467f000-b46a8000 r-xp 00000000 08:02 2164142    /usr/lib/libfontconfig.so.1.0.4
b46a8000-b46ad000 rw-p 00028000 08:02 2164142    /usr/lib/libfontconfig.so.1.0.4
b46ad000-b46ae000 rw-p b46ad000 00:00 0 
b46ae000-b4715000 r-xp 00000000 08:02 2164152    /usr/lib/libfreetype.so.6.3.10
b4715000-b4718000 rw-p 00067000 08:02 2164152    /usr/lib/libfreetype.so.6.3.10
b4718000-b4751000 r-xp 00000000 08:02 2164295    /usr/lib/libgobject-2.0.so.0.1200.4
b4751000-b4752000 rw-p 00038000 08:02 2164295    /usr/lib/libgobject-2.0.so.0.1200.4
b4752000-b4767000 r-xp 00000000 08:02 2163036    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b4767000-b4768000 rw-p 00015000 08:02 2163036    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b4768000-b4797000 r-xp 00000000 08:02 2164575    /usr/lib/librsvg-2.so.2.16.0
b4797000-b4798000 rw-p 0002f000 08:02 2164575    /usr/lib/librsvg-2.so.2.16.0
b4798000-b47f8000 r-xp 00000000 08:02 2164047    /usr/lib/libcairo.so.2.9.2
b47f8000-b47fa000 rw-p 0005f000 08:02 2164047    /usr/lib/libcairo.so.2.9.2
b47fa000-b47fb000 rw-s 00000000 00:08 3571724    /SYSV00000000 (deleted)
b47fb000-b47fe000 r-xp 00000000 08:02 2167457    /usr/lib/beryl/libneg.so
b47fe000-b47ff000 rw-p 00002000 08:02 2167457    /usr/lib/beryl/libneg.so
b47ff000-b4802000 r-xp 00000000 08:02 2167456    /usr/lib/beryl/libmove.so
b4802000-b4803000 rw-p 00003000 08:02 2167456    /usr/lib/beryl/libmove.so
b4803000-b4807000 r-xp 00000000 08:02 2167463    /usr/lib/beryl/libresize.so
b4807000-b4808000 rw-p 00004000 08:02 2167463    /usr/lib/beryl/libresize.so
b4808000-b480a000 r-xp 00000000 08:02 2167452    /usr/lib/beryl/libfade.so
b480a000-b480b000 rw-p 00001000 08:02 2167452    /usr/lib/beryl/libfade.so
b480b000-b4814000 r-xp 00000000 08:02 2167388    /usr/lib/beryl/libcube.so
b4814000-b4815000 rw-p 00009000 08:02 2167388    /usr/lib/beryl/libcube.so
b4815000-b4828000 r-xp 00000000 08:02 2166215    /usr/lib/beryl/libanimation.so
b4828000-b4829000 rw-p 00012000 08:02 2166215    /usr/lib/beryl/libanimation.so
b4829000-b6829000 rw-s 00000000 00:08 3506186    /SYSV00000000 (deleted)
b6829000-b682a000 rw-s 00000000 00:08 3473417    /SYSV00000000 (deleted)
b682a000-b682b000 rw-s 00000000 00:08 3440648    /SYSV00000000 (deleted)
b682b000-b686b000 rw-s ef42e000 00:0d 10103      /dev/nvidia0
b686b000-b696b000 rw-s 35641000 00:0d 10103      /dev/nvidia0
b696b000-b6aad000 rw-s 35579000 00:0d 10103      /dev/nvidia0
b6aad000-b6aee000 rw-p b6aad000 00:00 0 
b6aee000-b6b58000 rw-p 00000000 00:0d 1540       /dev/zero
b6b58000-b7058000 rw-s e0000000 00:0d 10103      /dev/nvidia0
b7058000-b7079000 rw-p b7058000 00:00 0 
b7079000-b709f000 rw-s 00000000 00:08 3080192    /SYSV00000000 (deleted)
b709f000-b70a7000 r-xp 00000000 08:02 2163947    /usr/lib/libXcursor.so.1.0.2
b70a7000-b70a8000 rw-p 00007000 08:02 2163947    /usr/lib/libXcursor.so.1.0.2
b70a8000-b70ac000 r-xp 00000000 08:02 2167455    /usr/lib/beryl/libinputzoom.so
b70ac000-b70ad000 rw-p 00003000 08:02 2167455    /usr/lib/beryl/libinputzoom.so
b70ad000-b70b0000 r-xp 00000000 08:02 2164255    /usr/lib/libgmodule-2.0.so.0.1200.4
b70b0000-b70b1000 rw-p 00002000 08:02 2164255    /usr/lib/libgmodule-2.0.so.0.1200.4
b70b1000-b70b5000 r-xp 00000000 08:02 2167448    /usr/lib/beryl/libdecoration.so
b70b5000-b70b6000 rw-p 00003000 08:02 2167448    /usr/lib/beryl/libdecoration.so
b70b6000-b70b8000 r-xp 00000000 08:02 2167387    /usr/lib/beryl/libcrashhandler.so
b70b8000-b70b9000 rw-p 00001000 08:02 2167387    /usr/lib/beryl/libcrashhandler.so
b70b9000-b70be000 r-xp 00000000 08:02 2195600    /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b70be000-b70bf000 rw-p 00004000 08:02 2195600    /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b70bf000-b70c8000 r-xp 00000000 08:02 1851424    /lib/tls/i686/cmov/libnss_files-2.4.so
b70c8000-b70ca000 rw-p 00008000 08:02 1851424    /lib/tls/i686/cmov/libnss_files-2.4.so
b70ca000-b70d2000 r-xp 00000000 08:02 1851426    /lib/tls/i686/cmov/libnss_nis-2.4.so
b70d2000-b70d4000 rw-p 00007000 08:02 1851426    /lib/tls/i686/cmov/libnss_nis-2.4.so
b70d4000-b70e6000 r-xp 00000000 08:02 1851421    /lib/tls/i686/cmov/libnsl-2.4.so
b70e6000-b70e8000 rw-p 00011000 08:02 1851421    /lib/tls/i686/cmov/libnsl-2.4.so
b70e8000-b70ea000 rw-p b70e8000 00:00 0 
b70ea000-b70eb000 rw-s 00000000 00:08 3538955    /SYSV00000000 (deleted)
b70eb000-b70ef000 rw-s 3563a000 00:0d 10103      /dev/nvidia0
b70ef000-b70f3000 r-xp 00000000 08:02 2164420    /usr/lib/beryl/backends/libini.so
b70f3000-b70f4000 rw-p 00003000 08:02 2164420    /usr/lib/beryl/backends/libini.so
b70f4000-b70fb000 r--s 00000000 08:02 507905     /usr/lib/gconv/gconv-modules.cache
b70fb000-b7165000 rw-p b70fb000 00:00 0 
b7165000-b7174000 r-xp 00000000 08:02 1851429    /lib/tls/i686/cmov/libpthread-2.4.so
b7174000-b7176000 rw-p 0000f000 08:02 1851429    /lib/tls/i686/cmov/libpthread-2.4.so
b7176000-b7178000 rw-p b7176000 00:00 0 
b7178000-b717c000 r-xp 00000000 08:02 2163951    /usr/lib/libXdmcp.so.6.0.0
b717c000-b717d000 rw-p 00003000 08:02 2163951    /usr/lib/libXdmcp.so.6.0.0
b717d000-b717f000 r-xp 00000000 08:02 2163942    /usr/lib/libXau.so.6.0.0
b717f000-b7180000 rw-p 00001000 08:02 2163942    /usr/lib/libXau.so.6.0.0
b7180000-b7181000 r-xp 00000000 08:02 2164022    /usr/lib/tls/libnvidia-tls.so.1.0.9742
b7181000-b7182000 rw-p 00000000 08:02 2164022    /usr/lib/tls/libnvidia-tls.so.1.0.9742
b7182000-b7ab0000 r-xp 00000000 08:02 2164287    /usr/lib/libGLcore.so.1.0.9742
b7ab0000-b7ae7000 rwxp 0092d000 08:02 2164287    /usr/lib/libGLcore.so.1.0.9742
b7ae7000-b7aec000 rwxp b7ae7000 00:00 0 
b7aec000-b7aed000 rw-p b7aec000 00:00 0 
b7aed000-b7af4000 r-xp 00000000 08:02 1851431    /lib/tls/i686/cmov/librt-2.4.so
b7af4000-b7af6000 rw-p 00006000 08:02 1851431    /lib/tls/i686/cmov/librt-2.4.so
b7af6000-b7b09000 r-xp 00000000 08:02 2164682    /usr/lib/libz.so.1.2.3
b7b09000-b7b0a000 rw-p 00012000 08:02 2164682    /usr/lib/libz.so.1.2.3
b7b0a000-b7b0c000 r-xp 00000000 08:02 1851418    /lib/tls/i686/cmov/libdl-2.4.so
b7b0c000-b7b0e000 rw-p 00001000 08:02 1851418    /lib/tls/i686/cmov/libdl-2.4.so
b7b0e000-b7b15000 r-xp 00000000 08:02 2163977    /usr/lib/libXrender.so.1.3.0
b7b15000-b7b16000 rw-p 00006000 08:02 2163977    /usr/lib/libXrender.so.1.3.0
b7b16000-b7b22000 r-xp 00000000 08:02 2163955    /usr/lib/libXext.so.6.4.0
b7b22000-b7b23000 rw-p 0000c000 08:02 2163955    /usr/lib/libXext.so.6.4.0
b7b23000-b7b24000 rw-p b7b23000 00:00 0 
b7b24000-b7bea000 r-xp 00000000 08:02 2163936    /usr/lib/libX11.so.6.2.0
b7bea000-b7bed000 rw-p 000c5000 08:02 2163936    /usr/lib/libX11.so.6.2.0
b7bed000-b7d1a000 r-xp 00000000 08:02 1851415    /lib/tls/i686/cmov/libc-2.4.so
b7d1a000-b7d1c000 r--p 0012c000 08:02 1851415    /lib/tls/i686/cmov/libc-2.4.so
b7d1c000-b7d1e000 rw-p 0012e000 08:02 1851415    /lib/tls/i686/cmov/libc-2.4.so
b7d1e000-b7d21000 rw-p b7d1e000 00:00 0 
b7d21000-b7d2e000 r-xp 00000000 08:02 2164315    /usr/lib/libberylsettings.so.0.0.0
b7d2e000-b7d2f000 rw-p 0000d000 08:02 2164315    /usr/lib/libberylsettings.so.0.0.0
b7d2f000-b7d53000 r-xp 00000000 08:02 1851419    /lib/tls/i686/cmov/libm-2.4.so
b7d53000-b7d55000 rw-p 00023000 08:02 1851419    /lib/tls/i686/cmov/libm-2.4.so
b7d55000-b7dcd000 r-xp 00000000 08:02 2164194    /usr/lib/libGL.so.1.0.9742
b7dcd000-b7de8000 rwxp 00077000 08:02 2164194    /usr/lib/libGL.so.1.0.9742
b7de8000-b7de9000 rwxp b7de8000 00:00 0 
b7de9000-b7e7a000 r-xp 00000000 08:02 2164243    /usr/lib/libglib-2.0.so.0.1200.4
b7e7a000-b7e7b000 rw-p 00091000 08:02 2164243    /usr/lib/libglib-2.0.so.0.1200.4
b7e7b000-b7e7c000 rw-p b7e7b000 00:00 0 
b7e7c000-b7e83000 r-xp 00000000 08:02 2164621    /usr/lib/libstartup-notification-1.so.0.0.0
b7e83000-b7e84000 rw-p 00006000 08:02 2164621    /usr/lib/libstartup-notification-1.so.0.0.0
b7e84000-b7e86000 r-xp 00000000 08:02 2163965    /usr/lib/libXinerama.so.1.0.0
b7e86000-b7e87000 rw-p 00001000 08:02 2163965    /usr/lib/libXinerama.so.1.0.0
b7e87000-b7e9c000 r-xp 00000000 08:02 2163914    /usr/lib/libICE.so.6.3.0
b7e9c000-b7e9d000 rw-p 00014000 08:02 2163914    /usr/lib/libICE.so.6.3.0
b7e9d000-b7e9f000 rw-p b7e9d000 00:00 0 
b7e9f000-b7ea7000 r-xp 00000000 08:02 2163932    /usr/lib/libSM.so.6.0.0
b7ea7000-b7ea8000 rw-p 00007000 08:02 2163932    /usr/lib/libSM.so.6.0.0
b7ea8000-b7eaa000 r-xp 00000000 08:02 2163975    /usr/lib/libXrandr.so.2.0.0
b7eaa000-b7eab000 rw-p 00002000 08:02 2163975    /usr/lib/libXrandr.so.2.0.0
b7eab000-b7eaf000 r-xp 00000000 08:02 2163957    /usr/lib/libXfixes.so.3.1.0
b7eaf000-b7eb0000 rw-p 00003000 08:02 2163957    /usr/lib/libXfixes.so.3.1.0
b7eb0000-b7eb1000 rw-p b7eb0000 00:00 0 
b7eb1000-b7eb3000 r-xp 00000000 08:02 2163949    /usr/lib/libXdamage.so.1.0.0
b7eb3000-b7eb4000 rw-p 00001000 08:02 2163949    /usr/lib/libXdamage.so.1.0.0
b7eb4000-b7eb6000 r-xp 00000000 08:02 2164990    /usr/lib/libXcomposite.so.1.0.0
b7eb6000-b7eb7000 rw-p 00001000 08:02 2164990    /usr/lib/libXcomposite.so.1.0.0
b7eb7000-b7eda000 r-xp 00000000 08:02 2163400    /usr/lib/libpng12.so.0.1.2.8
b7eda000-b7edb000 rw-p 00023000 08:02 2163400    /usr/lib/libpng12.so.0.1.2.8
b7edb000-b7edc000 rw-s ef46f000 00:0d 10103      /dev/nvidia0
b7edc000-b7edd000 rw-s 35638000 00:0d 10103      /dev/nvidia0
b7edd000-b7ede000 rw-s 35637000 00:0d 10103      /dev/nvidia0
b7ede000-b7edf000 rw-s fac02000 00:0d 10103      /dev/nvidia0
b7edf000-b7ee0000 rw-s fa001000 00:0d 10103      /dev/nvidia0
b7ee0000-b7ee7000 r-xp 00000000 08:02 1851422    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7ee7000-b7ee9000 rw-p 00006000 08:02 1851422    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7ee9000-b7eea000 rw-p b7ee9000 00:00 0 
b7eea000-b7eec000 rwxp 00000000 00:0d 1540       /dev/zero
b7eec000-b7eee000 rw-p b7eec000 00:00 0 
b7eee000-b7f07000 r-xp 00000000 08:02 1819203    /lib/ld-2.4.so
b7f07000-b7f09000 rw-p 00018000 08:02 1819203    /lib/ld-2.4.so
bfa68000-bfa9b000 rwxp bfa68000 00:00 0          [stack]
bfa9b000-bfa9d000 rw-p bfa9b000 00:00 0 
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
XGL Absent, checking for NVIDIA
Nvidia Present
Reloading options
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /usr/share/beryl/snowflake2-8.png
Initiating splash
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/beryl, process 5970
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libstartup-notification-1.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libGL.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /usr/lib/libberylsettings.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libberylsettings.so.0
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /usr/lib/libXrender.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libz.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /lib/tls/i686/cmov/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/libGLcore.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLcore.so.1
Reading symbols from /usr/lib/tls/libnvidia-tls.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/tls/libnvidia-tls.so.1
Reading symbols from /lib/ld-linux.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1223280944 (LWP 5970)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/beryl/backends/libini.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/backends/libini.so
Reading symbols from /usr/lib/X11/locale/common/xlibi18n.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/X11/locale/common/xlibi18n.so.2
Reading symbols from /usr/lib/libXcursor.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/beryl/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libanimation.so
Reading symbols from /usr/lib/beryl/libcrashhandler.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libcrashhandler.so
Reading symbols from /usr/lib/beryl/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libdecoration.so
Reading symbols from /usr/lib/beryl/libcube.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libcube.so
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/librsvg-2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libfreetype.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libgsf-1.so.114...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libxml2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libexpat.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/beryl/libinputzoom.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libinputzoom.so
Reading symbols from /usr/lib/beryl/libfade.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libfade.so
Reading symbols from /usr/lib/beryl/libgroup.so...done.
Loaded symbols for /usr/lib/beryl/libgroup.so
Reading symbols from /usr/lib/beryl/libresize.so...done.
Loaded symbols for /usr/lib/beryl/libresize.so
Reading symbols from /usr/lib/beryl/libmove.so...done.
Loaded symbols for /usr/lib/beryl/libmove.so
Reading symbols from /usr/lib/beryl/libneg.so...done.
Loaded symbols for /usr/lib/beryl/libneg.so
Reading symbols from /usr/lib/beryl/libplace.so...done.
Loaded symbols for /usr/lib/beryl/libplace.so
Reading symbols from /usr/lib/beryl/libpng.so...done.
Loaded symbols for /usr/lib/beryl/libpng.so
Reading symbols from /usr/lib/beryl/libput.so...done.
Loaded symbols for /usr/lib/beryl/libput.so
Reading symbols from /usr/lib/beryl/librotate.so...done.
Loaded symbols for /usr/lib/beryl/librotate.so
Reading symbols from /usr/lib/beryl/libscale.so...done.
Loaded symbols for /usr/lib/beryl/libscale.so
Reading symbols from /usr/lib/beryl/libthumbnail.so...done.
Loaded symbols for /usr/lib/beryl/libthumbnail.so
Reading symbols from /usr/lib/beryl/libsplash.so...done.
Loaded symbols for /usr/lib/beryl/libsplash.so
Reading symbols from /usr/lib/beryl/libsnow.so...done.
Loaded symbols for /usr/lib/beryl/libsnow.so
Reading symbols from /usr/lib/beryl/libswitcher.so...done.
Loaded symbols for /usr/lib/beryl/libswitcher.so
Reading symbols from /usr/lib/beryl/libsvg.so...done.
Loaded symbols for /usr/lib/beryl/libsvg.so
Reading symbols from /usr/lib/beryl/libwater.so...done.
Loaded symbols for /usr/lib/beryl/libwater.so
Reading symbols from /usr/lib/beryl/libwobbly.so...done.
Loaded symbols for /usr/lib/beryl/libwobbly.so
Reading symbols from /usr/lib/beryl/libtile.so...done.
Loaded symbols for /usr/lib/beryl/libtile.so
Reading symbols from /lib/libgcc_s.so.1...done.
Loaded symbols for /lib/libgcc_s.so.1

0xffffe410 in __kernel_vsyscall ()
(gdb) 
Thread 1 (Thread -1223280944 (LWP 5970)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c7b6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c23281 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
#3  0xb70b6de6 in getCompPluginInfo () from /usr/lib/beryl/libcrashhandler.so
#4  0xbfa988e8 in ?? ()
#5  0xb70b7230 in _fini () from /usr/lib/beryl/libcrashhandler.so
#6  <signal handler called>
#7  0xffffe410 in __kernel_vsyscall ()
#8  0xb7c16770 in raise () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7c17ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7c4bd0b in __fsetlocking () from /lib/tls/i686/cmov/libc.so.6
#11 0xb7c538bd in mallopt () from /lib/tls/i686/cmov/libc.so.6
#12 0xb7c53a44 in free () from /lib/tls/i686/cmov/libc.so.6
#13 0xb7b5df6d in XFree () from /usr/lib/libX11.so.6
#14 0xb441a59d in getWindowIconGeometry (w=0x820ebf8, ix=0xbfa998e0, 
    iy=0xbfa998dc, iw=0xbfa998d4, ih=0xbfa998d8) at thumbnail.c:347
	actual = 6
	result = 1
	format = 32
	n = 4
	left = 0
	data = (unsigned char *) 0x818a6d8 "0,\b\003"
	mydata = (long unsigned int *) 0x818a6d8
	winIconGeometryAtom = 422
#15 0xb441b4ac in thumbHandleEvent (d=0x807aba0, event=0xbfa99ffc)
    at thumbnail.c:716
	abort_hiding = 0
	w2 = 23068706
	mousex = 432
	xj = 432
	m = 16
	ix = 137158192
	mousey = 63
	yj = 63
	iy = 1003
	w1 = 421
	ih = 21
	iw = 122
	w = (CompWindow *) 0x820ebf8
	s = (CompScreen *) 0x8100730
	td = (ThumbDisplay *) 0x81d6738
#16 0xb440c8a7 in getCompPluginInfo () from /usr/lib/beryl/libswitcher.so
#17 0x0807aba0 in compDisplays ()
#18 0xbfa99ffc in ?? ()
#19 0xbfa99ffc in ?? ()
#20 0xb440343c in ?? () from /usr/lib/beryl/libwater.so
#21 0x0807aba0 in compDisplays ()
#22 0xbfa99ffc in ?? ()
#23 0xbfa99978 in ?? ()
#24 0xb43ffc98 in getCompPluginInfo () from /usr/lib/beryl/libwater.so
#25 0x0807aba0 in compDisplays ()
#26 0xbfa99ffc in ?? ()
#27 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c7b6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c23281 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
#3  0xb70b6de6 in getCompPluginInfo () from /usr/lib/beryl/libcrashhandler.so
#4  0xbfa988e8 in ?? ()
#5  0xb70b7230 in _fini () from /usr/lib/beryl/libcrashhandler.so
#6  <signal handler called>
#7  0xffffe410 in __kernel_vsyscall ()
#8  0xb7c16770 in raise () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7c17ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7c4bd0b in __fsetlocking () from /lib/tls/i686/cmov/libc.so.6
#11 0xb7c538bd in mallopt () from /lib/tls/i686/cmov/libc.so.6
#12 0xb7c53a44 in free () from /lib/tls/i686/cmov/libc.so.6
#13 0xb7b5df6d in XFree () from /usr/lib/libX11.so.6
#14 0xb441a59d in getWindowIconGeometry (w=0x820ebf8, ix=0xbfa998e0, 
    iy=0xbfa998dc, iw=0xbfa998d4, ih=0xbfa998d8) at thumbnail.c:347
#15 0xb441b4ac in thumbHandleEvent (d=0x807aba0, event=0xbfa99ffc)
    at thumbnail.c:716
#16 0xb440c8a7 in getCompPluginInfo () from /usr/lib/beryl/libswitcher.so
#17 0x0807aba0 in compDisplays ()
#18 0xbfa99ffc in ?? ()
#19 0xbfa99ffc in ?? ()
#20 0xb440343c in ?? () from /usr/lib/beryl/libwater.so
#21 0x0807aba0 in compDisplays ()
#22 0xbfa99ffc in ?? ()
#23 0xbfa99978 in ?? ()
#24 0xb43ffc98 in getCompPluginInfo () from /usr/lib/beryl/libwater.so
#25 0x0807aba0 in compDisplays ()
#26 0xbfa99ffc in ?? ()
#27 0x00000000 in ?? ()
Detaching from program: /usr/bin/beryl, process 5970

[CRASH_HANDLER]: "/tmp/beryl_crash-5970.out" created!

DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_info_read_metabat: assertion `*bats < max_bat || *bats >= BAT_MAGIC_METABAT' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_info_read_metabat: assertion `*bats < max_bat || *bats >= BAT_MAGIC_METABAT' failed

(/usr/lib/beagle/IndexHelper.exe:6214): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF

```

---

### Post by Sohum on 2007-01-18
Oh, and I'm doing this from w3m in recovery mode, as my other account does not have sudo privileges.

Just so you know.

---

### Post by allwin on 2007-01-18
Looks to me like Beryl crashed.  I've played around with this for about a month and see similar symptoms all the time.  Beryl's what, 0.1.4?  It's beta.  CTRL-ALT-BACKSPACE gets you back in terminal mode and you can startx up again or start GDM via sudo /etc/init.d/gdm restart.  Hint, you may want to take Beryl out as the window manager and use the Beryl settings to start it back up instead of loading it as a startup program for the session.  That way you have a little more control of things when they go boom.  I'm not enough of an expert to interpret the finer points of all those messages beyond noting that Beryl seems to be the culprit.  Maybe a future poster can shed more light on a more specific recommendation.

---

### Post by Sohum on 2007-01-18
a) Ctrl-Alt-Backspace does nothing. As I said, there's no response from any input device.
b) I don't think Beryl is the culprit, as Beryl seems to load fine and at times I can use it and move around the windows/cube. *Then* edgy crashes.
c) I think it is beagle, as beagle was taking up much of my cpu recently.
d) How do I edit startup programs of another account from the command line?

Thanks guys.

---

### Post by Canyonero on 2007-01-19
It very well could be Beryl. I just installed it yesterday, and when I try to start it, I get the following error in the terminal:

```
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
QFont::setPointSize: Point size <= 0 (-3)
trying '/home/<my user>/.xcompmgrrc' as configfile


finished parsing the config file
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

```

Any idea what this means though?

---

### Post by Sohum on 2007-01-19
I always get that or similar errors when starting graphical programs from the terminal. It has no effect; I always ignore it, and everything usually works.

To reiterate: Does anyone know how to edit the (Gnome) startup programs of an account from the terminal of another?

---

