---
title: "Samba keeps crashing (coring) when streaming to windows pc"
date: 2008-06-10
forum: General Help
---

### Post by whatever69 on 2008-06-10
I was happily listening to music off of my windows media centre pc which is connected to my ubuntu server with my girlfriend while eating ice cream, when this error happened:

  process_usershare_file: stat of /var/lib/samba/usershares/raid failed. Permission denied
[2008/06/10 22:04:17, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/raid failed. Permission denied
[2008/06/10 22:21:35, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/raid failed. Permission denied
[2008/06/10 22:30:21, 0] lib/substitute.c:alloc_sub_basic(463)
  alloc_sub_basic: NULL source string!  This should not happen
[2008/06/10 22:30:21, 0] lib/fault.c:fault_report(41)
  ===============================================================
[2008/06/10 22:30:21, 0] lib/fault.c:fault_report(42)
  INTERNAL ERROR: Signal 11 in pid 6855 (3.0.28a)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2008/06/10 22:30:21, 0] lib/fault.c:fault_report(44)
  
  From: [http://www.samba.org/samba/docs/Samba3-HOWTO.pdf](http://www.samba.org/samba/docs/Samba3-HOWTO.pdf)
[2008/06/10 22:30:21, 0] lib/fault.c:fault_report(45)
  ===============================================================
[2008/06/10 22:30:21, 0] lib/util.c:smb_panic(1633)
  PANIC (pid 6855): internal error
[2008/06/10 22:30:21, 0] lib/util.c:log_stack_trace(1737)
  BACKTRACE: 12 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x2d) [0x828ab6d]
   #1 /usr/sbin/smbd(smb_panic+0x5d) [0x828ac9d]
   #2 /usr/sbin/smbd [0x827551a]
   #3 [0xb7f10420]
   #4 /usr/sbin/smbd(volume_label+0x54) [0x809b314]
   #5 /usr/sbin/smbd(handle_trans2+0x25a) [0x80ecb8a]
   #6 /usr/sbin/smbd(reply_trans2+0x69c) [0x80f364c]
   #7 /usr/sbin/smbd [0x810f90e]
   #8 /usr/sbin/smbd(smbd_process+0x89b) [0x8110d6b]
   #9 /usr/sbin/smbd(main+0xa18) [0x835ec18]
   #10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b24450]
   #11 /usr/sbin/smbd [0x8094331]
[2008/06/10 22:30:21, 0] lib/util.c:smb_panic(1638)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 6855]
[2008/06/10 22:30:21, 0] lib/util.c:smb_panic(1646)
  smb_panic(): action returned status 0
[2008/06/10 22:30:21, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd
[2008/06/10 22:30:21, 1] smbd/service.c:make_connection_snum(1033)
  windowspc (192.168.0.107) connect to service raid initially as user roy (uid=1000, gid=1000) (pid 6909)

I actually get the permission denied quite a bit in the log files, and then the occasional core.  Is this the correct forum for this?  Any help would be appreciated.  I'm using:  

Linux ubuntuserver 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

When I type smbstatus, I get the following result:

root@ubuntuserver:/home/roy# smbstatus

Samba version 3.0.28a
PID     Username      Group         Machine                        
-------------------------------------------------------------------
 6909   roy           roy           windowspc    (192.168.0.107)

Service      pid     machine       Connected at
-------------------------------------------------------
raid         6909   windowspc     Tue Jun 10 22:30:21 2008

Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/1997-01-25 - Australia-Melbourne - Big Day Out Festival/1 Come To Daddy, Mummy Mix.mp3   Tue Jun 10 22:30:04 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/1997-09-17 - USA-Colorado-Denver - Ogden Theatre/1 intro.mp3   Tue Jun 10 22:30:05 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/1997-07-13 - Norway-Kristiansand - Quartfestivalen/01 radio intro.mp3   Tue Jun 10 22:30:03 2008
6909         1000       DENY_NONE  0x81        RDONLY     NONE             /mnt/raid   roy/audio/FullAlbums   Tue Jun 10 22:30:23 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/1993-04-09 - UK-England-Sheffield - Hallam University/1.mp3   Tue Jun 10 22:30:02 2008
6909         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Other/2006/IE Merg - Live at H272/Part 1.mp3   Tue Jun 10 22:37:54 2008
6855         1000       DENY_NONE  0x20089     RDONLY     NONE             /mnt/raid   roy/audio/winmx/x-ecutioners - Genius of Love 2002 (Featuring Tom Tom Club & Biz Markie).mp3   Tue Jun 10 22:27:56 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/1997-01-27 - Australia-Sydney - Big Day Out Festival.mp3   Tue Jun 10 22:30:04 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/2002-03-16 - USA-California-Los Angeles - All Tomorrow's Parties/14.mp3   Tue Jun 10 22:30:06 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/2002-12-15 - France-Saint Ouen - Les Mains D'oeuvres.mp3   Tue Jun 10 22:30:08 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/1997-06-29 - Denmark-Roskilde - Roskilde Festival/1 Laughable Butane Bob.mp3   Tue Jun 10 22:30:04 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/2003-04-08 - UK-England-East Sussex - Camber Sands - All Tomorrows Parties - BBC Radio 1 - DJ set 1.mp3   Tue Jun 10 22:30:09 2008
6909         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Unsorted/Mix-Master-Mike (Beastie Boys) @ DNA Lounge San Francisco 2005/mix master mike @ dna lounge - san-francisco.mp3   Tue Jun 10 22:37:52 2008
6909         1000       DENY_NONE  0x81        RDONLY     NONE             /mnt/raid   roy/audio   Tue Jun 10 22:30:23 2008
6909         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Other/2001/Live at Vancouver Jazz festival - Jun. 24  2001/01 Cinematic Orchestra_ Live Set 1.mp3   Tue Jun 10 22:38:01 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/2002-05-18 - Spain-Barcelona - Primavera Sound.mp3   Tue Jun 10 22:30:07 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/2003-11-06 - UK-Scotland-Glasgow - The Henrywood Hall.mp3   Tue Jun 10 22:30:10 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/2003-05-13 - All Tomorrows Parties - BBC Radio One - DJ set 2.mp3   Tue Jun 10 22:30:09 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Annie On One/LCD Soundsystem Magnetmen Deep Dish_Annie Nightingale/LCD Soundsystem, Magnetmen, Deep Dish AN 2006-01-06.mp3   Tue Jun 10 22:30:14 2008
6855         1000       DENY_NONE  0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/FullAlbums/90 90s Songs/AlbumArt_{4A5EFBA2-D22C-4330-A50C-2F56F94DD719}_Large.jpg   Tue Jun 10 22:30:21 2008
6909         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/FullAlbums/Jimi Hendrix - Live At Winterland/01-Prologue.mp3   Tue Jun 10 22:38:02 2008
6855         1000       DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /mnt/raid   roy/audio/Mixes/Artist/Aphex Twin/Aphex Twin Mega Torrent/Aphex twin-live sets from 1992-2006/2005-04-08 - Austria-Mayrhofen - Snowbombing.mp3   Tue Jun 10 22:30:12 2008



Any help would be appreciated!

---

### Post by whatever69 on 2008-06-11
I went and did chmod 775 -R on my entire share.  Looks like I had some files that weren't writable.  I've been streaming music now for 10+ hours.  So far no crashes.  Cross your fingers.  However, I think Samba should handles things a bit more gracefully.

Here's my testparm file.  Does anybody see any issues?  The intefaces entry perhaps?


roy@ubuntuserver:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = PEANUTS
        server string = %h server (Samba, Ubuntu)
        interfaces = eth0, 192.168.0.0/24
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        load printers = No
        printcap name = /dev/null
        disable spoolss = Yes
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        printing = bsd
        print command = lpr -r -P'%p' %s
        lpq command = lpq -P'%p'
        lprm command = lprm -P'%p' %j

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

---

