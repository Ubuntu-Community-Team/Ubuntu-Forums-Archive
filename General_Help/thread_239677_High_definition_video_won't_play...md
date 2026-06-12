---
title: "High definition video won't play.."
date: 2006-08-19
forum: General Help
---

### Post by Jeroen Vernooij on 2006-08-19
I'm having a problem with high definition video on dapper 6.06 gnome.
If I open totem or any other video-player and try to open a HD-video (and I tried more than one.. 3 with the same effect) the player instantly dissapears..

if I fire up totem from commandline, these are the errors:
```
jeroen@laptop:~$ totem
No accelerated IMDCT transform found
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 47 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

VLC gives this output:
```
jeroen@laptop:~$ vlc
VLC media player 0.8.4 Janus
[00000321] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

```

It seems that I don't have enough memory or something..

however, free -m gives this:
```
jeroen@laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           494        478         15          0          2        161
-/+ buffers/cache:        315        179
Swap:            0          0          0

```

Is that indeed too less?

As far as I know I have all the codecs installed (w32codecs, gstreamer, libdvdcss)
One of the files I'm trying to open is just 1280x720, 46.3 MB....

In Windows XP they play just fine..(wmp, VLC)

---

### Post by taurus on 2006-08-19
You don't have a swap space!!!

---

### Post by Jeroen Vernooij on 2006-08-19
Huh indeed, that's really weird because at the installation, I made a 500MB partition assigned to swap, and disk manager shows it actually IS swap right now. Booting linux shows something like 
setup swapfile .. ok

---

### Post by taurus on 2006-08-19
What does your /etc/fstab look like then?

```
more /etc/fstab
```

---

### Post by Jeroen Vernooij on 2006-08-20
/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

As far as I see this is just fine (looking to fstab's in other threads)

---

### Post by euclid on 2007-07-17
Ive got same problems seems one year on and noone has bothered to post an answer so much for Ubuntu being ready for prime time think Im going back to XP.

---

