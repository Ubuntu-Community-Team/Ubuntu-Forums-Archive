---
title: "DVDs not playing or working"
date: 2007-06-15
forum: General Help
---

### Post by Silenus on 2007-06-15
Whenever I try to play a dvd, it crashes totem, or says can not read from source or disk, user permissions, etc. And it was working a week or so ago, when I ripped a dvd of mine to my hd, but I can't find a reason for this now, can anyone help?

---

### Post by yabbadabbadont on 2007-06-15
If you are using totem-gstreamer, it will only play a dvd when the disc is autodetected after being inserted.  The ubuntu wiki suggests installing totem-xine instead.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Silenus on 2007-06-15
Yes but it is not just that it isn't opening it, it's that other applications such as acid rip seem to ignore it to, not even vlc player can play them. It's as if it is ignoring it entirely, I mean you can see it mount to desktop but that's about it.

---

### Post by yabbadabbadont on 2007-06-15
Read and follow the instructions in the wiki and see if it helps.  If not, post the exact error messages, if any, and the steps you took to get them.

---

### Post by Silenus on 2007-06-15
I followed all the instructions on it, and now when I try to play the dvd, totem just crashes, it says dvd menu, as if it's reading it, then it just crashes to desktop. No error.

---

### Post by yabbadabbadont on 2007-06-15
Open a terminal window and launch totem from there.  Perhaps there will be an error message displayed then.

---

### Post by Silenus on 2007-06-15
Well it left me with this

This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 72 error_code 8 request_code 141 minor_code 13)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

and at command line it says specified movie cant not be found and crashed gnome.

---

### Post by yabbadabbadont on 2007-06-15
Well, at this point I can only suggest trying one of the many other players to try to determine if the problem lies with totem or is more low level than that.  i.e.  If one or more of the others can play it then the problem is totem.  If none can, then there is something fundamentally wrong in the system.

You might try vlc, mplayer, gxine, or xine-ui to see if any of them will work.

---

### Post by Silenus on 2007-06-15
I tried vlc, nothing. And mplayer. idk what to do from here.

---

### Post by Silenus on 2007-06-15
I just tried gxine and I got this output

No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

---

### Post by Silenus on 2007-06-15
Ok I got one movie to work, but the others wont, attack of the clones seems to work fine.

---

### Post by Silenus on 2007-06-16
Ok I tried using vlc, to play a movie that worked about a week ago and I got this output


VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd1 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/george/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000008f8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000c65
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000d45
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00000d5f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00001c8d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00001d8e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x000043e9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00051d39
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003c641f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c6487
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003c88f0
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
[00000346] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

---

### Post by yabbadabbadont on 2007-06-16
Try running vlc using sudo and see if the problem goes away.  If it does, then there is a permissions problem somewhere.

---

### Post by psiu on 2007-06-16
The latest libdvdcss update poops on dvd playback--luckily its easy to rollback.
open a terminal window and enter:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Should be fine after that, may require a restart--I did because my dvd drive on the laptop is moody anyways.  Found this in this thread: [http://ubuntuforums.org/showthread.php?t=475432](http://ubuntuforums.org/showthread.php?t=475432)

---

### Post by chele on 2007-06-28
> **Silenus said:**
> Whenever I try to play a dvd, it crashes totem, or says can not read from source or disk, user permissions Take a look at [this]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550") bug. If you go to System - Preferences - Removable Drives and Media Preferences - Multimedia and set the Video DVD section to "gksudo totem %m", what happens?

---

### Post by Bablefish on 2007-06-28
You need the codecs that come when you install Automatrix

---

### Post by FredSambo on 2007-06-29
> **psiu said:**
> The latest libdvdcss update poops on dvd playback--luckily its easy to rollback.
open a terminal window and enter:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Should be fine after that, may require a restart--I did because my dvd drive on the laptop is moody anyways.  Found this in this thread: [http://ubuntuforums.org/showthread.php?t=475432](http://ubuntuforums.org/showthread.php?t=475432)

This helped me with the same problem!  I too have a touchy DVD drive (pioneer).

Thanks!

---

### Post by hmg on 2007-07-08
sudo /usr/share/doc/libdvdread3/install-css.sh

that worked for me only to open the menu. when i select "play", vlc vanishes.
any ideas?

---

