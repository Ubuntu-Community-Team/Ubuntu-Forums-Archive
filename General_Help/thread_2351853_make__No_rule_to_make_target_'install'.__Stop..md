---
title: "make: *** No rule to make target 'install'.  Stop."
date: 2017-02-07
forum: General Help
---

### Post by anonym777 on 2017-02-07
Hello, people

I want to install firmware modification kit in ubuntu in order to modify dd-wrt firmware. I did the following commands:
```
./configure

make
kea@ThinkPad-T43:~/Hentet/fmk/src$ make
make -C ./bff/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/bff'
gcc bff_huffman_decompress.c -o bff_huffman_decompress
bff_huffman_decompress.c: In function ‘unpack_parse_header’:
bff_huffman_decompress.c:167:14: **[COLOR=#800080]warning:[/COLOR]** implicit declaration of function ‘read’ [-Wimplicit-function-declaration]
  bytesread = read(in, hdr + prelen, PACK_HEADER_LENGTH - prelen);
              ^
bff_huffman_decompress.c: In function ‘unpack’:
bff_huffman_decompress.c:318:22: **[COLOR=#800080]warning: [/COLOR]**implicit declaration of function ‘dup’ [-Wimplicit-function-declaration]
  unpack_parse_header(dup(in), dup(out), pre, prelen, bytes_in, &unpackd);
                      ^
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/bff'
make -C ./uncramfs/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/uncramfs'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/uncramfs'
make -C ./uncramfs-lzma/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/uncramfs-lzma'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/uncramfs-lzma'
make -C ./cramfs-2.x/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/cramfs-2.x'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/cramfs-2.x'
make -C ./cramfsswap/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/cramfsswap'
strip cramfsswap
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/cramfsswap'
make -C ./squashfs-2.1-r2/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/squashfs-2.1-r2'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/squashfs-2.1-r2'
make -C ./squashfs-3.0/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/squashfs-3.0'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/squashfs-3.0'
make -C ./squashfs-3.0-lzma-damn-small-variant/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/squashfs-3.0-lzma-damn-small-variant'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/squashfs-3.0-lzma-damn-small-variant'
make -C ./wrt_vx_imgtool/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/wrt_vx_imgtool'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/kea/Hentet/fmk/src/wrt_vx_imgtool'
make -C ./others/
make[1]: Entering directory '/home/kea/Hentet/fmk/src/others'
make -C ./squashfs-3.0-e2100
make[2]: Entering directory '/home/kea/Hentet/fmk/src/others/squashfs-3.0-e2100'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/kea/Hentet/fmk/src/others/squashfs-3.0-e2100'
make -C ./squashfs-3.2-r2
make[2]: Entering directory '/home/kea/Hentet/fmk/src/others/squashfs-3.2-r2'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/kea/Hentet/fmk/src/others/squashfs-3.2-r2'
make -C ./squashfs-3.2-r2-lzma
make[2]: Entering directory '/home/kea/Hentet/fmk/src/others/squashfs-3.2-r2-lzma'

sudo make install
make: *** No rule to make target 'install'.  Stop.
```

Can anyone help me or tell me why I get this error?

Thank you in advance and have a lovely day!

---

### Post by wlbi on 2017-02-07
probably there is nothing for automatic installation. You have to install it by your own -)
Maybe teher are new files in [COLOR=#000000]/home/kea/Hentet/fmk/src
 or [/COLOR][COLOR=#000000]/home/kea/Hentet/fmk/

[/COLOR]

---

### Post by anonym777 on 2017-02-07
The only new file is Makefile.

These are all the files:

kea@ThinkPad-T43:~/Hentet/fmk/src$ ls
addpattern      cramfsswap      squashfs-2.1-r2
addpattern.c    crcalc          squashfs-3.0
addpattern.o    firmware-tools  squashfs-3.0-lzma-damn-small-variant
asustrx         jffs2           tpl-tool
asustrx.c       lzma            uncramfs
asustrx.o       Makefile        uncramfs-lzma
autom4te.cache  Makefile.in     untrx
bff             motorola-bin    untrx.cc
binwalk-1.0     motorola-bin.c  untrx.h
config.log      motorola-bin.o  untrx.o
config.status   others          webcomp-tools
configure       splitter3       wrt_vx_imgtool
configure.ac    splitter3.cc
cramfs-2.x      splitter3.o

---

### Post by anonym777 on 2017-02-07
There is no install rule in the Makefile. What to do?

---

