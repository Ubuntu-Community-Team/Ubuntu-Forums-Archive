---
title: "skipped frames"
date: 2005-09-08
forum: General Help
---

### Post by Copter on 2005-09-08
hi!

from some time i have problems with watching divx movies from my hard drive. i use vlc but the same thing happens when using kaffeine. i think its some kind of lib problem. it did not happen a month ago. since then i was trying to upgrade my Ati graphic drivers but with no luck. i switched to my previously saved x.org config file and everything went back to normal.

anyway when i run 'vlc -vvvv' (debug mode) i get this
```

...
[00000284] main video output debug: got 8 direct buffer(s)
[00000284] main video output debug: picture in 592x256, chroma 0x30323449 (I420), aspect ratio 37:16
[00000284] main video output debug: picture out 592x256, chroma 0x30323449 (I420), aspect ratio 37:16
[00000284] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000284] main video output debug: thread -1343079504 (video output) created at priority 0 (src/video_output/video_output.c:443)
[00000287] main audio output debug: thread -1353577552 (aout) created at priority 0 (alsa.c:603)
[00000240] main module debug: using audio output module "alsa"
[00000287] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000287] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[00000287] main audio output debug: no need for any filter
[00000287] main audio output debug: looking for audio mixer module
[00000287] main audio output debug: probing 3 candidates
[00000089] main module debug: using audio mixer module "float32_mixer"
[00000287] main audio output debug: input 'mpga' 48000 Hz Stereo frame=1152 samples/969 bytes
[00000287] main audio output debug: filter(s) 'mpga'->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[00000289] main private debug: looking for audio filter module
[00000289] main private debug: probing 23 candidates
[00000079] main module debug: using audio filter module "mpgatofixed32"
[00000287] main audio output debug: found a filter for the whole conversion
[00000287] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[00000292] main private debug: looking for audio filter module
[00000292] main private debug: probing 23 candidates
[00000076] main module debug: using audio filter module "bandlimited_resampler"
[00000287] main audio output debug: found a filter for the whole conversion
[00000284] xvideo video output debug: entering fullscreen mode
[00000284] main video output warning: late picture skipped (128487)
[00000284] main video output warning: late picture skipped (86835)
[00000284] main video output warning: late picture skipped (45142)
[00000284] main video output warning: late picture skipped (3445)
[00000284] main video output warning: late picture skipped (467284)
[00000284] main video output warning: late picture skipped (425634)
[00000284] main video output warning: late picture skipped (383944)
[00000284] main video output warning: late picture skipped (342262)
[00000284] main video output warning: late picture skipped (300568)
[00000284] main video output warning: late picture skipped (258873)
[00000284] main video output warning: late picture skipped (242244)
[00000284] main video output warning: late picture skipped (200598)
[00000284] main video output warning: late picture skipped (158903)
[00000284] main video output warning: late picture skipped (138767)
[00000284] main video output warning: late picture skipped (97108)
[00000284] main video output warning: late picture skipped (55427)
[00000284] main video output warning: late picture skipped (37182)
[00000284] main video output warning: late picture skipped (450227)
[00000284] main video output warning: late picture skipped (408576)
[00000284] main video output warning: late picture skipped (366885)
[00000284] main video output warning: late picture skipped (325203)
[00000284] main video output warning: late picture skipped (283510)
[00000284] main video output warning: late picture skipped (241815)
[00000284] main video output warning: late picture skipped (249600)
[00000284] main video output warning: late picture skipped (207970)
[00000284] main video output warning: late picture skipped (166292)
[00000284] main video output warning: late picture skipped (124598)
[00000284] main video output warning: late picture skipped (82904)
[00000284] main video output warning: late picture skipped (65064)
[00000284] main video output warning: late picture skipped (23415)
[00000284] main video output warning: late picture skipped (3715)
[00000284] main video output warning: late picture skipped (458812)
[00000284] main video output warning: late picture skipped (417161)
[00000284] main video output warning: late picture skipped (375472)
[00000284] main video output warning: late picture skipped (333777)
[00000284] main video output warning: late picture skipped (292094)
[00000284] main video output warning: late picture skipped (250400)
[00000284] main video output warning: late picture skipped (232269)
[00000284] main video output warning: late picture skipped (212461)
[00000284] main video output warning: late picture skipped (170830)
[00000284] main video output warning: late picture skipped (151036)
[00000284] main video output warning: late picture skipped (109381)
[00000284] main video output warning: late picture skipped (89610)
[00000284] main video output warning: late picture skipped (69914)
[00000284] main video output warning: late picture skipped (28272)
[00000284] xvideo video output debug: leaving fullscreen mode
[00000284] main video output warning: late picture skipped (78435)
[00000284] main video output warning: late picture skipped (36813)
[00000284] main video output warning: late picture skipped (84947)
[00000284] main video output warning: late picture skipped (43306)
[00000284] main video output warning: late picture skipped (1617)
[00000284] main video output warning: late picture skipped (62941)
[00000284] main video output warning: late picture skipped (21290)
[00000284] main video output warning: late picture skipped (64168)
[00000284] main video output warning: late picture skipped (22527)
[00000284] main video output warning: late picture skipped (73345)
[00000284] main video output warning: late picture skipped (31695)

```

it skips some frames about every 10 seconds. anyone know what can cause this "main video output warning: late picture skipped"?

btw, when i run the same movie in normal mode i see this

```

[00000283] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:128

```so it looks ok, it is not the matter of one file. all movies act the same.

thanks for help!
copter :]

---

### Post by rafakl on 2005-09-08
did you enabled direct memory access (DMA) in your dvd drive??

use:

sudo hdparm -d1 [your dvd location]

for example:

sudo hdparm -d1 /dev/hdc

you must edit your /etc/hdparm.conf file if you want to leave it enabled everytime you boot your computer.

---

### Post by Copter on 2005-09-09
thanks for hint but i think its not DMA issue. i run the movies from SATA NTFS partitions (dma on) or USB HDD FAT32 (seen as SCSI, no DMA thing). my DVD has got also dma enabled.

although i can _hear_ that when the frames are skipped some data is being read from HDD at the moment.

copter :]

EDIT: the same thing happens when watching DVD movies...

---

### Post by Copter on 2005-09-17
damn, it has got to be some global problem. the same thing happens when running divx / mpeg / avi / dvd movies using vlc / kaffeine. everything acts the same. i tried newest ati drivers and default ubuntu ones. nothing changes.

anyone, please help. i have to swich to windows to watch movies :(

copter :]

---

