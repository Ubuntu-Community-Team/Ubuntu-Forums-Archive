---
title: "problem with zlib1g"
date: 2007-02-25
forum: General Help
---

### Post by kito on 2007-02-25
I usually don't hit up the forums for help but this one's got me stumped and I'm sure it's something obvious. I'm trying to install recordmydesktop from source, which depends on zlib.h. I've got zlib1g and zlib1g-dev installed, and zlib.h is in /usr/include/. I tried to compile the following test file:

```

#include <zlib.h>

int main()
{
  unsigned int len;
  voidp buf;
  gzFile file;
  gzread( file, buf, len );
}

```

and I get the following result

```

$ gcc test.c 
/tmp/cc64k6Bh.o: In function `main':
test.c:(.text+0x14): undefined reference to `gzread'
collect2: ld returned 1 exit status

```

Like I said, it seems like it would be something obvious, but I'm just not seeing it right now. For those interested, the output from running make on recordmydesktop.

```

$ make
make  all-recursive
make[1]: Entering directory `/home/kito/recordmydesktop-0.3.3.1'
Making all in src
make[2]: Entering directory `/home/kito/recordmydesktop-0.3.3.1/src'
gcc  -g -O2   -o recordmydesktop -lSM -lICE recordmydesktop-recordmydesktop.o recordmydesktop-getzpixmap.o recordmydesktop-parseargs.o recordmydesktop-rectinsert.o recordmydesktop-setbrwindow.o recordmydesktop-queryextensions.o recordmydesktop-register_callbacks.o recordmydesktop-get_frame.o recordmydesktop-update_image.o recordmydesktop-poll_damage.o recordmydesktop-encode_image_buffer.o recordmydesktop-bgr_to_yuv.o recordmydesktop-flush_to_ogg.o recordmydesktop-make_dummy_pointer.o recordmydesktop-opendev.o recordmydesktop-capture_sound.o recordmydesktop-encode_sound_buffer.o recordmydesktop-init_encoder.o recordmydesktop-cache_frame.o recordmydesktop-cache_audio.o recordmydesktop-rmd_cache.o recordmydesktop-load_cache.o recordmydesktop-wm_check.o recordmydesktop-encode_cache.o recordmydesktop-rmdthreads.o recordmydesktop-initialize_data.o recordmydesktop-rmd_jack.o  -lpthread -ltheora -logg -lvorbisenc -lvorbisfile -lvorbis -lXdamage -lXfixes -lXext -lX11 -lSM -lICE -lm 
recordmydesktop-cache_frame.o: In function `FlushBlock':
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:79: undefined reference to `gzwrite'
recordmydesktop-cache_frame.o: In function `CacheImageBuffer':
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:219: undefined reference to `gzsetparams'
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:232: undefined reference to `gzwrite'
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:221: undefined reference to `gzsetparams'
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:236: undefined reference to `gzwrite'
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:235: undefined reference to `gzwrite'
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:234: undefined reference to `gzwrite'
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:315: undefined reference to `gzflush'
/home/kito/recordmydesktop-0.3.3.1/src/cache_frame.c:316: undefined reference to `gzclose'
recordmydesktop-rmd_cache.o: In function `InitCacheData':
/home/kito/recordmydesktop-0.3.3.1/src/rmd_cache.c:167: undefined reference to `gzopen'
recordmydesktop-rmd_cache.o: In function `SwapCacheFilesRead':
/home/kito/recordmydesktop-0.3.3.1/src/rmd_cache.c:64: undefined reference to `gzclose'
/home/kito/recordmydesktop-0.3.3.1/src/rmd_cache.c:65: undefined reference to `gzopen'
recordmydesktop-rmd_cache.o: In function `SwapCacheFilesWrite':
/home/kito/recordmydesktop-0.3.3.1/src/rmd_cache.c:47: undefined reference to `gzflush'
/home/kito/recordmydesktop-0.3.3.1/src/rmd_cache.c:48: undefined reference to `gzclose'
/home/kito/recordmydesktop-0.3.3.1/src/rmd_cache.c:49: undefined reference to `gzopen'
recordmydesktop-load_cache.o: In function `LoadCache':
/home/kito/recordmydesktop-0.3.3.1/src/load_cache.c:156: undefined reference to `gzopen'
/home/kito/recordmydesktop-0.3.3.1/src/load_cache.c:192: undefined reference to `gzread'
recordmydesktop-load_cache.o: In function `ReadZF':
/home/kito/recordmydesktop-0.3.3.1/src/load_cache.c:54: undefined reference to `gzread'
collect2: ld returned 1 exit status
make[2]: *** [recordmydesktop] Error 1
make[2]: Leaving directory `/home/kito/recordmydesktop-0.3.3.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kito/recordmydesktop-0.3.3.1'
make: *** [all] Error 2

```

my system: 
```

$ uname -a
Linux theBox 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

```

---

### Post by iovar on 2007-02-25
Hi kito,


```
gcc  -g -O2   -o recordmydesktop -lSM -lICE 
...
-lpthread -ltheora -logg -lvorbisenc -lvorbisfile -lvorbis -lXdamage -lXfixes -lXext -lX11 -lSM -lICE -lm

```

The above line should also have -lz
Also your example should be compiled with:
gcc test.c -lz 

My guess is that when you've run the configure script, you didn't have zlib1g-dev,
but it didn't exit with failure because I've forgotten to add AC_MSG_ERROR on the 
zlib check.
Installing zlib-dev later doesn't help as the Makefiles are already written.

So what you need to do is, run ./configure again and check the part where it says
```
checking for deflate in -lz... yes
```
(it should be yes)


Then run make again and this time it should compile.



John

---

### Post by kito on 2007-03-01
Thanks, that did it. I've never used autoconf to setup a project so I didn't think to check that.

---

