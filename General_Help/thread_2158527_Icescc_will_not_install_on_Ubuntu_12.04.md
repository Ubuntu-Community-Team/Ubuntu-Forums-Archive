---
title: "Icescc will not install on Ubuntu 12.04"
date: 2013-06-29
forum: General Help
---

### Post by helyos on 2013-06-29
As i saw many users have this error.


mkdir .libs
gcc -O20 -ffast-math -D_REENTRANT -fsigned-char -DUSE_MEMORY_H -o .libs/decoder_example decoder_example.o  ../lib/.libs/libvorbis.so -Wl,--rpath -Wl,/usr/local/centovacast/ices//lib
/usr/bin/ld: decoder_example.o: undefined reference to symbol 'ogg_stream_packetout'
/usr/bin/ld: note: 'ogg_stream_packetout' is defined in DSO /usr/local/centovacast/ices//lib/libogg.so.0 so try adding it to the linker command line
/usr/local/centovacast/ices//lib/libogg.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [decoder_example] Error 1
make[2]: Leaving directory `/usr/local/src/ices/libvorbis-1.1.2/examples'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/ices/libvorbis-1.1.2'
make: *** [all] Error 2
Make failed for libvorbis.tar.gz; aborting
Installer exited with error, aborting


How can be this solved? Please help us. I am a beginner .

---

