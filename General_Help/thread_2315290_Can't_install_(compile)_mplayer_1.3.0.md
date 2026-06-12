---
title: "Can't install (compile) mplayer 1.3.0"
date: 2016-02-27
forum: General Help
---

### Post by samp-rp-fan on 2016-02-27
hi everyone

i'm trying to install new version of mplayer on ubuntu 14.04, but there is no binary packages, so i thought maybe it won't be too hard to compile it from source

./configure worked fine, but when i try 'make' command there is error message in console:
```

ffmpeg/libavcodec/libavcodec.a(utils.o): In function `default_lockmgr_cb':
utils.c:(.text+0x14e): undefined reference to `__sync_val_compare_and_swap_4'
utils.c:(.text+0x1d2): undefined reference to `__sync_val_compare_and_swap_4'
ffmpeg/libavcodec/libavcodec.a(utils.o): In function `av_register_hwaccel':
utils.c:(.text+0x68f5): undefined reference to `__sync_val_compare_and_swap_4'
ffmpeg/libavcodec/libavcodec.a(utils.o): In function `ff_lock_avcodec':
utils.c:(.text+0x6a5a): undefined reference to `__sync_add_and_fetch_4'
ffmpeg/libavcodec/libavcodec.a(utils.o): In function `ff_codec_open2_recursive':
utils.c:(.text+0x81ef): undefined reference to `__sync_add_and_fetch_4'
ffmpeg/libavcodec/libavcodec.a(utils.o): In function `avcodec_register':
utils.c:(.text.unlikely+0xc2): undefined reference to `__sync_val_compare_and_swap_4'
ffmpeg/libavformat/libavformat.a(format.o): In function `av_register_input_format':
format.c:(.text+0x59): undefined reference to `__sync_val_compare_and_swap_4'
ffmpeg/libavformat/libavformat.a(format.o): In function `av_register_output_format':
format.c:(.text+0xa9): undefined reference to `__sync_val_compare_and_swap_4'
ffmpeg/libavcodec/libavcodec.a(bitstream_filter.o): In function `av_register_bitstream_filter':
bitstream_filter.c:(.text+0x39): undefined reference to `__sync_val_compare_and_swap_4'
ffmpeg/libavcodec/libavcodec.a(parser.o): In function `av_register_codec_parser':
parser.c:(.text+0x39): undefined reference to `__sync_val_compare_and_swap_4'
ffmpeg/libavutil/libavutil.a(buffer.o): In function `buffer_replace':
buffer.c:(.text+0x48): undefined reference to `__sync_add_and_fetch_4'
ffmpeg/libavutil/libavutil.a(buffer.o): In function `pool_release_buffer':
buffer.c:(.text+0xb9): undefined reference to `__sync_add_and_fetch_4'
ffmpeg/libavutil/libavutil.a(buffer.o): In function `av_buffer_unref':
buffer.c:(.text+0x40e): undefined reference to `__sync_add_and_fetch_4'
ffmpeg/libavutil/libavutil.a(buffer.o): In function `av_buffer_make_writable':
buffer.c:(.text+0x550): undefined reference to `__sync_add_and_fetch_4'
ffmpeg/libavutil/libavutil.a(buffer.o): In function `av_buffer_realloc':
buffer.c:(.text+0x6c4): undefined reference to `__sync_add_and_fetch_4'
ffmpeg/libavutil/libavutil.a(buffer.o):buffer.c:(.text+0x88f): more undefined references to `__sync_add_and_fetch_4' follow
collect2: error: ld returned 1 exit status
make: *** [mplayer] Error 1

```

can anyone help me with this problem please?


upd: solved, thanks for your replies!

---

### Post by SeijiSensei on 2016-02-27
I recommend just using the packages in Doug McMahon's PPA for Trusty: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

You might want to give mpv a try, since it is the successor to mplayer.

Did you run
```
sudo apt-get build-dep mplayer
```
first before compiling?  That will install any needed libraries and header files.

---

### Post by mc4man on 2016-02-27
Not sure what you mean by mplayer 1.3.0, typically to build you'd do a svn checkout, then when configuring mplayer would retrieve the latest ffmpeg git.
Your errors seem to be from incompatible ffmpeg & mplayer.

If you want a new mplayer for trusty & don't care about mencoder then see here - 
[https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test](https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test)

Only updated now every rare once & a while as mplayer isn't being that actively developed any more & myself prefer mpv.

---

