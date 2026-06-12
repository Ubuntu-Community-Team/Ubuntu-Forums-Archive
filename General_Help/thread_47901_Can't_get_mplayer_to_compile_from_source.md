---
title: "Can't get mplayer to compile from source"
date: 2005-07-10
forum: General Help
---

### Post by delltony on 2005-07-10
I have been trying for the life of me to get mplayer to compile from the source on their page so it will include libmp3lame support.
I have installed lame and all and when i run ./configure it shows i have lame support
but i keep getting a problem i'm assuming with the video card.
please lookat this error log thanks. I'm out of ideas and the .deb file that is offered on the repositories does not include libmp3 support

> cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o pulse.o pulse.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o rvlc.o rvlc.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_dct.o sbr_dct.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_dec.o sbr_dec.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_e_nf.o sbr_e_nf.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_fbt.o sbr_fbt.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_hfadj.o sbr_hfadj.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_hfgen.o sbr_hfgen.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_huff.o sbr_huff.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_qmf.o sbr_qmf.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_syntax.o sbr_syntax.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o sbr_tf_grid.o sbr_tf_grid.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o specrec.o specrec.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o ssr.o ssr.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o ssr_fb.o ssr_fb.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o ssr_ipqf.o ssr_ipqf.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o syntax.o syntax.c
cc -c -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -o tns.o tns.c
ar r libfaad2.a bits.o cfft.o common.o decoder.o drc.o error.o filtbank.o hcr.o huffman.o ic_predict.o is.o lt_predict.o mdct.o mp4.o ms.o output.o pns.o ps_dec.o ps_syntax.o  pulse.o rvlc.o sbr_dct.o sbr_dec.o sbr_e_nf.o sbr_fbt.o sbr_hfadj.o sbr_hfgen.o sbr_huff.o sbr_qmf.o sbr_syntax.o sbr_tf_grid.o specrec.o ssr.o ssr_fb.o ssr_ipqf.o syntax.o tns.o
ar: creating libfaad2.a
true libfaad2.a
make[1]: Leaving directory `/home/delltony/Desktop/MPlayer-1.0pre7/libfaad2'
make -C tremor
make[1]: Entering directory `/home/delltony/Desktop/MPlayer-1.0pre7/tremor'
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o bitwise.o bitwise.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o block.o block.c
block.c: In function `vorbis_synthesis_init':
block.c:155: warning: assignment discards qualifiers from pointer target type
block.c:156: warning: assignment discards qualifiers from pointer target type
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o codebook.o codebook.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o floor0.o floor0.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o floor1.o floor1.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o framing.o framing.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o info.o info.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o mapping0.o mapping0.c
mapping0.c: In function `mapping0_inverse':
mapping0.c:297: warning: passing arg 2 of `_vorbis_apply_window' from incompatible pointer type
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o mdct.o mdct.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o registry.o registry.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o res012.o res012.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o sharedbook.o sharedbook.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o synthesis.o synthesis.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I..   -o window.o window.c
ar r libvorbisidec.a bitwise.o block.o codebook.o floor0.o floor1.o framing.o info.o mapping0.o mdct.o registry.o res012.o sharedbook.o synthesis.o window.o
ar: creating libvorbisidec.a
true libvorbisidec.a
make[1]: Leaving directory `/home/delltony/Desktop/MPlayer-1.0pre7/tremor'
make -C libdha
make[1]: Entering directory `/home/delltony/Desktop/MPlayer-1.0pre7/libdha'
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o libdha.o libdha.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o mtrr.o mtrr.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o pci.o pci.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o pci_names.o pci_names.c
#cc -shared -Wl,-soname,libdha.so.1 -o libdha.so.1.0  libdha.o mtrr.o pci.o pci_names.o 
cc -shared -Wl,-soname -Wl,libdha.so.1.0  -o libdha.so.1.0  libdha.o mtrr.o pci.o pci_names.o 
ln -sf libdha.so.1.0  libdha.so.1
ln -sf libdha.so.1.0  libdha.so
make[1]: Leaving directory `/home/delltony/Desktop/MPlayer-1.0pre7/libdha'
make -C vidix
make[1]: Entering directory `/home/delltony/Desktop/MPlayer-1.0pre7/vidix'
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -o vidixlib.o vidixlib.c
ar r libvidix.a vidixlib.o
ar: creating libvidix.a
true libvidix.a
make[2]: Entering directory `/home/delltony/Desktop/MPlayer-1.0pre7/vidix/drivers'
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o cyberblade_vid.o cyberblade_vid.c
cc -shared cyberblade_vid.o -L../../libdha -ldha -lm -Wl,-soname,cyberblade_vid.so -o cyberblade_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o radeon_vid.o radeon_vid.c
cc -shared radeon_vid.o -L../../libdha -ldha -lm -lGL  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lnsl -Wl,-soname,radeon_vid.so -o radeon_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -DRAGE128 -o rage128_vid.o radeon_vid.c
cc -shared rage128_vid.o -L../../libdha -ldha -lm -lGL  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lnsl -Wl,-soname,rage128_vid.so -o rage128_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -DRAGE128 -o mach64_vid.o mach64_vid.c
cc -shared mach64_vid.o -L../../libdha -ldha -Wl,-soname,mach64_vid.so -o mach64_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I..  -o nvidia_vid.o nvidia_vid.c
cc -shared nvidia_vid.o -L../../libdha -ldha -lm -Wl,-soname,nvidia_vid.so -o nvidia_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o mga_vid.o mga_vid.c
cc -shared mga_vid.o -L../../libdha -ldha -lm -Wl,-soname,mga_vid.so -o mga_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -DCRTC2 -o mga_crtc2_vid.o mga_vid.c
cc -shared mga_crtc2_vid.o -L../../libdha -ldha -lm -Wl,-soname,mga_crtc2_vid.so -o mga_crtc2_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o pm3_vid.o pm3_vid.c
cc -shared pm3_vid.o -L../../libdha -ldha -Wl,-soname,pm3_vid.so -o pm3_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o sis_vid.o sis_vid.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o sis_bridge.o sis_bridge.c
cc -shared sis_vid.o sis_bridge.o -L../../libdha -ldha -Wl,-soname,sis_vid.so -o sis_vid.so 
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o unichrome_vid.o unichrome_vid.c
cc -shared unichrome_vid.o -L../../libdha -ldha -lm -Wl,-soname,unichrome_vid.so -o unichrome_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -fPIC -I. -I.. -o savage_vid.o savage_vid.c
savage_vid.c:550:2: warning: #warning enable this again
savage_vid.c:578:2: warning: #warning is this needed?
cc -shared savage_vid.o -L../../libdha -ldha -lm -Wl,-soname,savage_vid.so -o savage_vid.so
make[2]: Leaving directory `/home/delltony/Desktop/MPlayer-1.0pre7/vidix/drivers'
make[1]: Leaving directory `/home/delltony/Desktop/MPlayer-1.0pre7/vidix'
make -C libmpdvdkit2
make[1]: Entering directory `/home/delltony/Desktop/MPlayer-1.0pre7/libmpdvdkit2'
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o css.o css.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o device.o device.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o dvd_input.o dvd_input.c
dvd_input.c: In function `DVDInputSetup':
dvd_input.c:139: warning: assignment from incompatible pointer type
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o dvd_reader.o dvd_reader.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o dvd_udf.o dvd_udf.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o error.o error.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o ifo_print.o ifo_print.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o ifo_read.o ifo_read.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o ioctl.o ioctl.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o libdvdcss.o libdvdcss.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o nav_print.o nav_print.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_MPLAYER  -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o nav_read.o nav_read.c
ar rc libmpdvdkit.a css.o device.o dvd_input.o dvd_reader.o dvd_udf.o error.o ifo_print.o ifo_read.o ioctl.o libdvdcss.o nav_print.o nav_read.o
true libmpdvdkit.a
make[1]: Leaving directory `/home/delltony/Desktop/MPlayer-1.0pre7/libmpdvdkit2'
cc -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium4 -mcpu=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/freetype2   -I/usr/include/SDL -D_REENTRANT -I/usr/X11R6/include       -o mplayer mplayer.o mp_msg.o cpudetect.o codec-cfg.o spudec.o playtree.o playtreeparser.o asxparser.o vobsub.o subreader.o sub_cc.o find_sub.o m_config.o m_option.o parser-cfg.o m_struct.o edl.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a  vidix/libvidix.a  libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a input/libinput.a postproc/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit libavcodec/libavcodec.a libavformat/libavformat.a  -lmad -ldv   -llzo -ldivxdecore -lmp3lame  -lxvidcore -lm  -lpng -lz -lz -ljpeg -lasound -ldl -lpthread   -lfreetype -lz -ltermcap -lcdda_interface -lcdda_paranoia -lliveMedia -lgroupsock -lUsageEnvironment -lBasicUsageEnvironment -lstdc++  -lnsl  -lungif  -lsmbclient  -lfontconfig    libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a  -laa -lGL  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lnsl -L/usr/lib -lSDL -lpthread -lggi   -lvgagl -lvga -lm   -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm  -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl       -lpthread -ldl -rdynamic   -lm
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x3a): In function `__static_initialization_and_destruction_0(int, int)':
: undefined reference to `operator*(short, DelayInterval const&)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x73): In function `__static_initialization_and_destruction_0(int, int)':
: undefined reference to `operator*(short, DelayInterval const&)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xac): In function `__static_initialization_and_destruction_0(int, int)':
: undefined reference to `operator*(short, DelayInterval const&)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x18a): In function `demux_open_rtp':
: undefined reference to `BasicTaskScheduler::createNew()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x1ac): In function `demux_open_rtp':
: undefined reference to `BasicUsageEnvironment::createNew(TaskScheduler&)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x1fb): In function `demux_open_rtp':
: undefined reference to `MediaSession::createNew(UsageEnvironment&, char const*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x26d): In function `demux_open_rtp':
: undefined reference to `MediaSubsessionIterator::MediaSubsessionIterator[in-charge](MediaSession&)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x279): In function `demux_open_rtp':
: undefined reference to `MediaSubsessionIterator::next()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x2d7): In function `demux_open_rtp':
: undefined reference to `MediaSubsession::initiate(int)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x35b): In function `demux_open_rtp':
: undefined reference to `increaseReceiveBufferTo(UsageEnvironment&, int, unsigned)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x3ba): In function `demux_open_rtp':
: undefined reference to `RTSPClient::setupMediaSubsession(MediaSubsession&, unsigned, unsigned)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x3fd): In function `demux_open_rtp':
: undefined reference to `RTSPClient::playMediaSession(MediaSession&, float, float, float)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x411): In function `demux_open_rtp':
: undefined reference to `MediaSubsessionIterator::reset()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x421): In function `demux_open_rtp':
: undefined reference to `MediaSubsessionIterator::next()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x543): In function `demux_open_rtp':
: undefined reference to `MediaSubsessionIterator::~MediaSubsessionIterator [in-charge]()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x5cf): In function `demux_open_rtp':
: undefined reference to `MediaSubsessionIterator::~MediaSubsessionIterator [in-charge]()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x5ed): In function `demux_open_rtp':
: undefined reference to `SIPClient::sendACK()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x635): In function `demux_open_rtp':
: undefined reference to `RTSPClient::createNew(UsageEnvironment&, int, char const*, unsigned short)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x677): In function `demux_open_rtp':
: undefined reference to `RTSPClient::describeWithPassword(char const*, char const*, char const*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x6d4): In function `demux_open_rtp':
: undefined reference to `RTSPClient::describeURL(char const*, Authenticator*, unsigned)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x727): In function `demux_open_rtp':
: undefined reference to `SIPClient::createNew(UsageEnvironment&, unsigned char, char const*, int, char const*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x772): In function `demux_open_rtp':
: undefined reference to `SIPClient::inviteWithPassword(char const*, char const*, char const*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x793): In function `demux_open_rtp':
: undefined reference to `SIPClient::invite(char const*, Authenticator*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0x7bb): In function `demux_open_rtp':
: undefined reference to `MediaSubsessionIterator::~MediaSubsessionIterator [in-charge]()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xa46): In function `demux_close_rtp':
: undefined reference to `Medium::close(Medium*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xa51): In function `demux_close_rtp':
: undefined reference to `Medium::close(Medium*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xa5c): In function `demux_close_rtp':
: undefined reference to `Medium::close(Medium*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xa84): In function `demux_close_rtp':
: undefined reference to `UsageEnvironment::reclaim()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xbc1): In function `getBuffer(demuxer_st*, demux_stream_t*, unsigned, float&)':
: undefined reference to `FramedSource::getNextFrame(unsigned char*, unsigned, void (*)(void*, unsigned, unsigned, timeval, unsigned), void*, void (*)(void*), void*)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xc98): In function `teardownRTSPorSIPSession(RTPState*)':
: undefined reference to `SIPClient::sendBYE()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xcaa): In function `teardownRTSPorSIPSession(RTPState*)':
: undefined reference to `MediaSubsessionIterator::MediaSubsessionIterator[in-charge](MediaSession&)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xcb2): In function `teardownRTSPorSIPSession(RTPState*)':
: undefined reference to `MediaSubsessionIterator::next()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xcc5): In function `teardownRTSPorSIPSession(RTPState*)':
: undefined reference to `RTSPClient::teardownMediaSubsession(MediaSubsession&)'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xccf): In function `teardownRTSPorSIPSession(RTPState*)':
: undefined reference to `MediaSubsessionIterator::~MediaSubsessionIterator [in-charge]()'
libmpdemux/libmpdemux.a(demux_rtp.o)(.text+0xcdb): In function `teardownRTSPorSIPSession(RTPState*)':
: undefined reference to `MediaSubsessionIterator::~MediaSubsessionIterator [in-charge]()'
libmpdemux/libmpdemux.a(demux_rtp_codec.o)(.text+0x201): In function `rtpCodecInitialize_video(demuxer_st*, MediaSubsession*, unsigned&)':
: undefined reference to `parseGeneralConfigStr(char const*, unsigned&)'
libmpdemux/libmpdemux.a(demux_rtp_codec.o)(.text+0x562): In function `rtpCodecInitialize_audio(demuxer_st*, MediaSubsession*, unsigned&)':
: undefined reference to `parseGeneralConfigStr(char const*, unsigned&)'
libmpdemux/libmpdemux.a(demux_rtp_codec.o)(.text+0x59d): In function `rtpCodecInitialize_audio(demuxer_st*, MediaSubsession*, unsigned&)':
: undefined reference to `parseStreamMuxConfigStr(char const*, unsigned&)'
/usr/lib/libBasicUsageEnvironment.a(DelayQueue.o)(.gnu.linkonce.t.__tf15DelayQueueEntry+0x2b): In function `DelayQueueEntry type_info function':
: undefined reference to `__rtti_user'
/usr/lib/libBasicUsageEnvironment.a(DelayQueue.o)(.gnu.linkonce.t.__tf10DelayQueue+0x3b): In function `DelayQueue type_info function':
: undefined reference to `__rtti_user'
/usr/lib/libBasicUsageEnvironment.a(DelayQueue.o)(.gnu.linkonce.t.__tf10DelayQueue+0x54): In function `DelayQueue type_info function':
: undefined reference to `__rtti_si'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

---

### Post by Naky on 2005-07-10
You're not the only one, I can't compile either build 5 or 7 for mplayer either and I was following that multimedia guide on the other forum too.

---

### Post by delltony on 2005-07-10
If you do happen to get it to work please let me know cause thats the same guide i was following. The only thing i can guess is that mplayer is wanting xf86vid and we are using xorg. Not possitive on that being the issue but it seems that way.  
If you run across a .deb file that has lame already compiled into it then post me the url. If you find a working solution regardless it being mencoder transcode dvd::rip dvd2divx ripdvd any of those let me know. I have tried them all wth no luck. The dvd2divx one kinda works but the avimux is an issue with ubuntu. Always some kinda issue.
Transcode will not install and i have installed every dependency i can find to satisfy it. so dvd::rip will not work

mencoder works fine if  i use ac3 instead of lame but the point is good quality at low diskspace ac3 is huge.

thanks,
tony

---

### Post by brahm on 2005-07-11
Had the same problem on both my PIII and AMD64 boxes. Took me a while to figure out the problem. First thought it was a problem with xvid. 

Make sure you install xlibmesa-dev, along with most of the other libxff86 development packages, especially libxxf86vm-dev.

Got both pre6 and pre7 to build after a lot of frustration!

Hope this helps!  :)

---

### Post by delltony on 2005-07-11
[QUOTE=brahm]Had the same problem on both my PIII and AMD64 boxes. Took me a while to figure out the problem. First thought it was a problem with xvid. 

Make sure you install xlibmesa-dev, along with most of the other libxff86 development packages, especially libxxf86vm-dev.

Got both pre6 and pre7 to build after a lot of frustration!

Hope this helps!  :)[/QUOTE]

thanks for the help still no go.

basically the same error but it doesn't take as long to produce the error now.
[http://pastebin.com/311398](http://pastebin.com/311398)

---

### Post by brahm on 2005-07-12
[QUOTE=delltony]thanks for the help still no go.

basically the same error but it doesn't take as long to produce the error now.
[http://pastebin.com/311398](http://pastebin.com/311398)[/QUOTE]

Try installing a meta-package called "x-window-system-dev". If it doesn't install the headers needed double-check on the following packages:
libxxf86vm-dev
libxxf86rush-dev
libxxf86misc-dev
libxxf86dga-dev

Before trying to compile again, run 'make distclean' and './configure' again.

Have uninstalled the above, got the same error message again, re-installed & did a successful compilation (with xvid support).

---

### Post by delltony on 2005-07-13
[QUOTE=brahm]Try installing a meta-package called "x-window-system-dev". If it doesn't install the headers needed double-check on the following packages:
libxxf86vm-dev
libxxf86rush-dev
libxxf86misc-dev
libxxf86dga-dev

Before trying to compile again, run 'make distclean' and './configure' again.

Have uninstalled the above, got the same error message again, re-installed & did a successful compilation (with xvid support).[/QUOTE]

Okay, thanks i just seen you follow up post today weds 7-13-05. I will try it and let you know what the outcome is. I was finally able to get transcode to install (the problem is if you use marillet at all it will bork)  I got rid of all the marillet stuff and trancode compiled smoothly. I use a script now called "ripmake" that is very nice in terms of transcoding its all shell based so i can run it remotely thru ssh on my other system while I use my main one for doing whatever.

Thanks for your help by the way I will keep you posted.

---

