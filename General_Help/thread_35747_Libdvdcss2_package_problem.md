---
title: "Libdvdcss2 package problem"
date: 2005-05-20
forum: General Help
---

### Post by ganatronic on 2005-05-20
Are there any instances where there is more to installing this package than just adding it through synaptic or 'sudo apt-get install libdvdcss2'?

I ask because I still seem to be having problems relating to it. It's definitely installed - see attached image, which also shows an error message.

I've tried using totem-xine, xine-ui, ogle, vlc, and now kaffeine - and my error is essentially the same for all: scrambled screen-related malfunction. 

In totem-xine and xine-ui, the video loads in a very obviously scrambled format. In ogle and vlc, the program closes itself immediately after I try and choose a chapter to watch. The menu loads up fine, however - but I'm guessing the menu is not encrypted. I can actually view chapters in vlc by using the Navigation tab to jump directly to them (which isn't so cool, because they are only labeled by number). In kaffeine, I get a handy error message when I try to choose a chapter (see attached image). I'm guessing log files from the other attempts would show a similar thing. But, uh, I don't yet know how to keep log files like that..

I've symlinked dev/hdc to dev/dvd. I've turned dma on. I have w32codecs, ffmpeg, gstreamer0.8-plugins. And I've read and reread all kinds of guides and threads.

Here's my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

(sorry, not sure how to retain formatting when pasting from terminal ...and hrm, not sure why my newly mounted hda3 isn't showing there...I'll figure that out later).

uname =  2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686 GNU/Linux

Could it have to do with me using 686? My video driver (s3 Unichrome Integrated)? Need any more info?

---

### Post by ganatronic on 2005-05-20
More information/questions:

Could it be that my dma is not enabled correctly?

I realize now that when I first read the "DVD Video" section on this [Restricted Formats Wiki](http://www.ubuntulinux.org/wiki/RestrictedFormats/view?searchterm=dvd%20playback) I manually went into /etc/hdparm.conf and removed the #'s by the hdc info, and then also changed "dma = off" to "dma = on". I then typed 'sudo /sbin/hdparm -d 1 /dev/hdc' in terminal. So I think I'll revert /etc/hdparm.conf back to how it was, and then just run the command again from terminal. (I'm at work right now; can't do this 'til later).

Still, though, that seems like a longshot. Does anyone know if there are drive permissions that might be affecting my playability?

Pretty much everything I read states how libdvdcss will fix my problems, but it's not. I don't need to, like, restart the computer, do I?

---

### Post by ganatronic on 2005-05-21
Yeah my idea from my last reply didn't do the trick.

But the good news is that I made some bug reports! Yippee!

Does this help? 

Log file for VLC (in parts):

```
VLC media player 0.8.1 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: FUTURAMA_S3_D1
libdvdnav: DVD Serial Number: 2F919310
libdvdnav: DVD Title (Alternative): FUTURAMA_S3_D1
libdvdnav: Unable to find map file '/home/ganatronic/.dvdnav/FUTURAMA_S3_D1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
``` 

It then gets 11 keys (VTS). Next:

```
libdvdnav: Suspected RCE Region Protection!!!
[00000268] xvideo video output warning: no free XVideo port found for format 0x3 0323449 (I420)
[00000268] xvideo video output warning: no free XVideo port found for format 0x3 2595559 (YUY2)
[00000268] xvideo video output warning: no free XVideo port found for format 0x3 6315652 (RV16)
[00000272] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000275] main private warning: dts != current_pts (313414)
[00000275] main private warning: backward_pts != current_pts (-33367)
[00000268] main video output warning: late picture skipped (17577)
No accelerated IMDCT transform found
[00000273] main audio output warning: PTS is out of range (196207), dropping buf fer
``` 

The audio output warning repeats for a while (my sound sounds fine - though I have xmms working its magic at the moment. maybe it's a conflict or something). And here's the end:

```
[00000238] main input warning: Program doesn't contain anymore ES, TODO cleaning  ?
[00000304] xvideo video output warning: no free XVideo port found for format 0x3 0323449 (I420)
[00000304] xvideo video output warning: no free XVideo port found for format 0x3 2595559 (YUY2)
[00000304] xvideo video output warning: no free XVideo port found for format 0x3 6315652 (RV16)
[00000306] main private warning: dts != current_pts (79538)
[00000302] spudec decoder warning: unknown command 0xa7
Segmentation fault
``` 


Okay, now for the Xine report. I have a handy BUG REPORT text file. Unfortunately it's 44kb, and the limit for attaching txt files is 20kb. Here's some snippets that I hope are possibly important. The full file, if you want, [can be viewed here](http://www.sacred-doily.com/report/BUG-REPORT.TXT).

```
xine: found input plugin  : DVD Navigator
libdvdnav: Using dvdnav version 1.0 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdcss debug: opening target `/dev/dvd'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key with player keys
libdvdcss debug: decrypted disc key is 03:a5:64:13:16
libdvdcss debug: using CSS key cache dir: /home/ganatronic/.dvdcss//FUTURAMA_S3_D1#2003121718123200/
libdvdcss error: failed opening raw device, continuing
libdvdnav: DVD Title: FUTURAMA_S3_D1
libdvdnav: DVD Serial Number: 2F919310
libdvdnav: DVD Title (Alternative): FUTURAMA_S3_D1
libdvdnav: Unable to find map file '/home/ganatronic/.dvdnav/FUTURAMA_S3_D1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
``` 

etc.

```
xine: found demuxer plugin: DVD/VOB demux plugin
video discontinuity #2, type is 0, disc_off 0
waiting for audio discontinuity #2
audio discontinuity #2, type is 0, disc_off 0
waiting for in_discontinuity update #2
vpts adjusted with prebuffer to 2113860
av_offset=0 pts
spu_offset=0 pts
xine_play
play_internal ...done
libdvdnav: Suspected RCE Region Protection!!!
load_plugins: plugin dxr3-spudec failed to instantiate itself.
load_plugins: plugin spudec will be used for spu streamtype 00.
Menu handle alloc failed. No more overlays objects available. Only 5 at once please.load_plugins:
``` 

and finally:

```
Menu handle alloc failed. No more overlays objects available. Only 5 at once please.Menu handle alloc failed. No more overlays objects available. Only 5 at once please.Menu handle alloc failed. No more overlays objects available. Only 5 at once please.Menu handle alloc failed. No more overlays objects available. Only 5 at once please.Menu handle alloc failed. No more overlays objects available. Only 5 at once please.ao_flush (loop running: 1)
libdvdcss error: no key but found encrypted block
libdvdcss error: no key but found encrypted block
Menu handle alloc failed. No more overlays objects available. Only 5 at once please.demux_mpeg_block: warning: PES header indicates that this stream may be encrypted (encryption mode 1)
video discontinuity #12, type is 2, disc_off 45045
waiting for audio discontinuity #12
audio_decoder: error, unknown buffer type: 02000000
audio_decoder: error, unknown buffer type: 04000000
audio_decoder: error, unknown buffer type: 01060000
audio_decoder: suggested switching to stream_id 00
audio discontinuity #12, type is 2, disc_off 45045
waiting for in_discontinuity update #12

---------------------- (ERROR) ----------------------
The source seems encrypted, and can't be read.
Your DVD is probably crypted. According to your country laws, you can or can't install/use libdvdcss to be able to read this disc, which you bought. (Media stream scrambled/encrypted)

['Encrypted media stream detected' 'Media stream scrambled/encrypted']
------------------ (END OF ERROR) -------------------


---------------------- (ERROR) ----------------------
The source seems encrypted, and can't be read.
Your DVD is probably crypted. According to your country laws, you can or can't install/use libdvdcss to be able to read this disc, which you bought. (Media stream scrambled/encrypted)

['Encrypted media stream detected' 'Media stream scrambled/encrypted']
------------------ (END OF ERROR) -------------------
``` 

That last part is an error message that pops up.

Libdvdcss seems to decrypt it, but then it runs into an encryption error anyway.
So, uh, can anyone help me? :eek:

---

