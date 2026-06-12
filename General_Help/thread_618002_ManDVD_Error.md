---
title: "ManDVD Error"
date: 2007-11-19
forum: General Help
---

### Post by tameree on 2007-11-19
Hi,

I'm running Ubuntu Gutsy Gibbon and I have trouble with the program ManDVD. Everything works well until i come to the encoding part. After 5 seconds i get an error message. Here is the console input:

--> Lancement de la génération du menu ------------------------------------------------------------
/home/gab/VidÃ©os/Projet Prison Break//menu.sh: line 2: cd: /home/gab/Vidéos/Projet Prison Break/: Aucun fichier ou rÃ©pertoire de ce type
1920+0 enregistrements lus
1920+0 enregistrements Ã©crits
7680 octets (7,7 kB) copiÃ©s, 0,0041016 seconde, 1,9 MB/s
Assuming raw pcm input file
LAME: Can't get "TERM" environment string.
LAME 3.97 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: 
MMX (ASM used)
, 3DNow! (ASM used)
, SSE
, SSE2

Using polyphase lowpass filter, transition band: 16452 Hz - 17032 Hz
Encoding /dev/stdin to silent.mpa
Encoding as 48 kHz 128 kbps j-stereo MPEG-1 Layer III (12x) qval=3

    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
     0/       ( 0%)|    0:00/     :  |    0:00/     :  |         x|     :  

     0/2      ( 0%)|    0:00/    0:00|    0:00/    0:00|   0.0000x|    0:00 

     4/4     (100%)|    0:00/    0:00|    0:00/    0:00|   0.0000x|    0:00 

jpegtopnm: 
Can't open normal.jpg.  Errno=No such file or directory(2).

pnmscale: 
EOF / read error reading magic number

   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  30000:1001
   INFO: [ppmtoy4m]     pixel aspect ratio:  10:11
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  top-field-first (interleaved PPM input)
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  1, or until input exhausted
   INFO: [ppmtoy4m]     chroma subsampling:  4:2:0 MPEG-2 (horiz. cositing)
**ERROR: [ppmtoy4m] Failed to read first frame.
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: system error (failed read/write)!
   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
**ERROR: [mplex] Unable to open file genmenu.m2v for reading.
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

/home/gab/VidÃ©os/Projet Prison Break//menu.sh: line 7: 10190 Exit 1                  mplex -f 8 -o /dev/stdout ${1}.m2v silent.mpa
     10191 Erreur de segmentation  (core dumped) | spumux -m dvd -v 2 ${1}.xml > ${1}.mpg

Does anybody have an idea on what i could do?

Thanks !

---

