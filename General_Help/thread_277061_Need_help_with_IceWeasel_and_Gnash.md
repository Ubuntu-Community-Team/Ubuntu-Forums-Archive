---
title: "Need help with IceWeasel and Gnash"
date: 2006-10-13
forum: General Help
---

### Post by joshua neff on 2006-10-13
Hey, folks! I've installed IceWeasel, but when I try to automatically install Gnash, it fails. I assume it's because I need to open IceWeasel as root, but everytime I try to do that, it fails, too. (I've tried *gksudo iceweasel*, *gksudo Iceweasel32*, and every combination of capitalization and not, with and without the "32", that I can think of. I can't seem to open IceWeasel as root. If someone can tell me a way to open IceWeasel as root that actually works, I'd be very grateful.)

But I've downloaded Gnash-0.7.1. I can unpack it, no problem. But what folder should I put it in so that IceWeasel will find it and use it?

---

### Post by pay on 2006-10-14
umm how about gksudo /path/to/gnash

---

### Post by joshua neff on 2006-10-14
> **pay said:**
> umm how about gksudo /path/to/gnash

No, I don't want to run Gnash, I want to know what folder to put it in so that IceWeasel will use it. :confused: 

(But I did try *gksudo /path/to/iceweasel* and it opened IceWeasel as root. Unfortunately, it still didn't automatically install Gnash.)

---

### Post by tturrisi on 2006-10-14
[http://www.gnu.org/software/gnash/manual/gnash.html#install](http://www.gnu.org/software/gnash/manual/gnash.html#install)

---

### Post by pay on 2006-10-14
Before I meant to write```
gksudo path/to/ice/weasel
```I don't know why I wrote gnash:confused: my head was off with the fairies.

---

### Post by joshua neff on 2006-10-14
> **pay said:**
> Before I meant to write```
gksudo path/to/ice/weasel
```I don't know why I wrote gnash:confused: my head was off with the fairies.

Heh. No problem.

---

### Post by joshua neff on 2006-10-14
> **tturrisi said:**
> [http://www.gnu.org/software/gnash/manual/gnash.html#install](http://www.gnu.org/software/gnash/manual/gnash.html#install)

Ah, this is helpful, thanks. I'm reading the Install doc in the Gnash folder. Unfortunately, after installing the required packages for configuration, everything after that isn't working.

The instructions say to type *make*, but when I type that, I get *bash: make: command not found*. Is there something I'm missing here?

---

### Post by joshua neff on 2006-10-14
I just tried the whole thing again, and yeah, *configure* seems to go right, but *make* still doesn't do anything. I'm really not sure what's going wrong.

---

### Post by Arisna on 2006-10-14
It sounds like you don't have a compiler installed if make doesn't work.  Try installing the package build-essential.

---

### Post by joshua neff on 2006-10-14
> **Arisna said:**
> It sounds like you don't have a compiler installed if make doesn't work.  Try installing the package build-essential.

YES! That did it! Thank you!

But when I run *make*, I get a string of errors. The same happens when I type *make install*. Would it help if I copied and pasted the errors here?

---

### Post by joshua neff on 2006-10-16
This is what it says when I run *make*:

> make  all-recursive
make[1]: Entering directory `/home/josh/Desktop/gnash-0.7.1'
Making all in libbase
make[2]: Entering directory `/home/josh/Desktop/gnash-0.7.1/libbase'
if /bin/sh ../libtool --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I. -I.. -I../server -I/usr/include  -I/usr/include/libxml2  -I/usr/include/SDL -I/usr/include/SDL    -DQT_THREAD_SUPPORT  -D_REENTRANT -I.. -I. -I.. -I../server -I/usr/include  -I/usr/include/libxml2  -I/usr/include/SDL -I/usr/include/SDL   -g -O2 -Wall -MT jpeg.lo -MD -MP -MF ".deps/jpeg.Tpo" -c -o jpeg.lo jpeg.cpp; \
        then mv -f ".deps/jpeg.Tpo" ".deps/jpeg.Plo"; else rm -f ".deps/jpeg.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I. -I.. -I../server -I/usr/include -I/usr/include/libxml2 -I/usr/include/SDL -I/usr/include/SDL -DQT_THREAD_SUPPORT -D_REENTRANT -I.. -I. -I.. -I../server -I/usr/include -I/usr/include/libxml2 -I/usr/include/SDL -I/usr/include/SDL -g -O2 -Wall -MT jpeg.lo -MD -MP -MF .deps/jpeg.Tpo -c jpeg.cpp  -fPIC -DPIC -o .libs/jpeg.o
jpeg.cpp:18:21: error: jpeglib.h: No such file or directory
jpeg.cpp:37: error: field 'm_pub' has incomplete type
jpeg.cpp:41: error: 'JOCTET' does not name a type
jpeg.cpp:60: error: 'j_decompress_ptr' has not been declared
jpeg.cpp:66: error: 'boolean' does not name a type
jpeg.cpp:111: error: 'j_decompress_ptr' has not been declared
jpeg.cpp:131: error: 'j_decompress_ptr' has not been declared
jpeg.cpp: In constructor 'jpeg::rw_source::rw_source(tu_file*)':
jpeg.cpp:51: error: 'm_pub' was not declared in this scope
jpeg.cpp:52: error: 'fill_input_buffer' was not declared in this scope
jpeg.cpp:54: error: 'jpeg_resync_to_restart' was not declared in this scope
jpeg.cpp: In static member function 'static void jpeg::rw_source::init_source(int)':
jpeg.cpp:62: error: base operand of '->' is not a pointer
jpeg.cpp: In static member function 'static void jpeg::rw_source::skip_input_data(int, long int)':
jpeg.cpp:115: error: base operand of '->' is not a pointer
jpeg.cpp:121: error: 'struct jpeg::rw_source' has no member named 'm_pub'
jpeg.cpp:122: error: 'struct jpeg::rw_source' has no member named 'm_pub'
jpeg.cpp:123: error: 'fill_input_buffer' was not declared in this scope
jpeg.cpp:126: error: 'struct jpeg::rw_source' has no member named 'm_pub'
jpeg.cpp:127: error: 'struct jpeg::rw_source' has no member named 'm_pub'
jpeg.cpp: In member function 'void jpeg::rw_source::discard_partial_buffer()':
jpeg.cpp:151: error: 'm_pub' was not declared in this scope
jpeg.cpp: In function 'void jpeg::setup_rw_source(jpeg_decompress_struct*, tu_file*)':
jpeg.cpp:162: error: invalid use of undefined type 'struct jpeg_decompress_struct'
jpeg.h:15: error: forward declaration of 'struct jpeg_decompress_struct'
jpeg.cpp: At global scope:
jpeg.cpp:170: error: field 'm_pub' has incomplete type
jpeg.cpp:173: error: 'JOCTET' does not name a type
jpeg.cpp:190: error: 'j_compress_ptr' has not been declared
jpeg.cpp:199: error: 'boolean' does not name a type
jpeg.cpp:218: error: 'j_compress_ptr' has not been declared
jpeg.cpp: In constructor 'jpeg::rw_dest::rw_dest(tu_file*)':
jpeg.cpp:182: error: 'm_pub' was not declared in this scope
jpeg.cpp:183: error: 'empty_output_buffer' was not declared in this scope
jpeg.cpp:186: error: 'm_buffer' was not declared in this scope
jpeg.cpp: In static member function 'static void jpeg::rw_dest::init_destination(int)':
jpeg.cpp:192: error: base operand of '->' is not a pointer
jpeg.cpp:195: error: 'struct jpeg::rw_dest' has no member named 'm_pub'
jpeg.cpp:195: error: 'struct jpeg::rw_dest' has no member named 'm_buffer'
jpeg.cpp:196: error: 'struct jpeg::rw_dest' has no member named 'm_pub'
jpeg.cpp: In static member function 'static void jpeg::rw_dest::term_destination(int)':
jpeg.cpp:222: error: base operand of '->' is not a pointer
jpeg.cpp:226: error: 'struct jpeg::rw_dest' has no member named 'm_pub'
jpeg.cpp:228: error: 'struct jpeg::rw_dest' has no member named 'm_buffer'
jpeg.cpp:237: error: base operand of '->' is not a pointer
jpeg.cpp: At global scope:
jpeg.cpp:242: error: variable or field 'setup_rw_dest' declared void
jpeg.cpp:242: error: 'int jpeg::setup_rw_dest' redeclared as different kind of symbol
jpeg.cpp:27: error: previous declaration of 'void jpeg::setup_rw_dest(jpeg_compress_struct*, tu_file*)'
jpeg.cpp:242: error: 'j_compress_ptr' was not declared in this scope
jpeg.cpp:242: error: expected primary-expression before '*' token
jpeg.cpp:242: error: 'outstream' was not declared in this scope
jpeg.cpp:255: error: variable or field 'jpeg_error_exit' declared void
jpeg.cpp:255: error: 'j_common_ptr' was not declared in this scope
jpeg.cpp:257: error: expected ',' or ';' before '{' token
jpeg.cpp:264: error: variable or field 'setup_jpeg_err' declared void
jpeg.cpp:264: error: 'jpeg_error_mgr' was not declared in this scope
jpeg.cpp:264: error: 'jerr' was not declared in this scope
jpeg.cpp:266: error: expected ',' or ';' before '{' token
jpeg.cpp:284: error: field 'm_cinfo' has incomplete type
jpeg.cpp:285: error: field 'm_jerr' has incomplete type
jpeg.cpp: In constructor 'jpeg::input_impl::input_impl(tu_file*)':
jpeg.cpp:299: error: 'm_jerr' was not declared in this scope
jpeg.cpp:299: error: 'jpeg::setup_jpeg_err' cannot be used as a function
jpeg.cpp:300: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:303: error: 'jpeg_create_decompress' was not declared in this scope
jpeg.cpp: In constructor 'jpeg::input_impl::input_impl(jpeg::input_impl::SWF_DEFINE_BITS_JPEG2_HEADER_ONLY, tu_file*)':
jpeg.cpp:321: error: 'm_jerr' was not declared in this scope
jpeg.cpp:321: error: 'jpeg::setup_jpeg_err' cannot be used as a function
jpeg.cpp:322: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:325: error: 'jpeg_create_decompress' was not declared in this scope
jpeg.cpp:330: error: 'FALSE' was not declared in this scope
jpeg.cpp:330: error: 'jpeg_read_header' was not declared in this scope
jpeg.cpp: In destructor 'virtual jpeg::input_impl::~input_impl()':
jpeg.cpp:341: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:346: error: 'jpeg_destroy_decompress' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::input_impl::discard_partial_buffer()':
jpeg.cpp:355: error: 'm_cinfo' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::input_impl::start_image()':
jpeg.cpp:379: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:379: error: 'FALSE' was not declared in this scope
jpeg.cpp:379: error: 'jpeg_read_header' was not declared in this scope
jpeg.cpp:380: error: 'JPEG_HEADER_TABLES_ONLY' was not declared in this scope
jpeg.cpp:381: error: 'JPEG_HEADER_OK' was not declared in this scope
jpeg.cpp:383: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:383: error: 'jpeg_start_decompress' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::input_impl::finish_image()':
jpeg.cpp:391: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:391: error: 'jpeg_finish_decompress' was not declared in this scope
jpeg.cpp: In member function 'virtual int jpeg::input_impl::get_height() const':jpeg.cpp:400: error: 'm_cinfo' was not declared in this scope
jpeg.cpp: In member function 'virtual int jpeg::input_impl::get_width() const':
jpeg.cpp:407: error: 'm_cinfo' was not declared in this scope
jpeg.cpp: In member function 'int jpeg::input_impl::get_components() const':
jpeg.cpp:416: error: 'm_cinfo' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::input_impl::read_scanline(unsigned char*)':
jpeg.cpp:426: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:427: error: 'jpeg_read_scanlines' was not declared in this scope
jpeg.cpp:431: error: 'JCS_GRAYSCALE' was not declared in this scope
jpeg.cpp: At global scope:
jpeg.cpp:473: error: field 'm_cinfo' has incomplete type
jpeg.cpp:474: error: field 'm_jerr' has incomplete type
jpeg.cpp: In constructor 'jpeg::output_impl::output_impl(tu_file*, int, int, int)':
jpeg.cpp:480: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:480: error: 'm_jerr' was not declared in this scope
jpeg.cpp:480: error: 'jpeg_std_error' was not declared in this scope
jpeg.cpp:483: error: 'jpeg_create_compress' was not declared in this scope
jpeg.cpp:489: error: 'JCS_RGB' was not declared in this scope
jpeg.cpp:490: error: 'jpeg_set_defaults' was not declared in this scope
jpeg.cpp:491: error: 'TRUE' was not declared in this scope
jpeg.cpp:491: error: 'jpeg_set_quality' was not declared in this scope
jpeg.cpp:493: error: 'jpeg_start_compress' was not declared in this scope
jpeg.cpp: In destructor 'virtual jpeg::output_impl::~output_impl()':
jpeg.cpp:500: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:500: error: 'jpeg_finish_compress' was not declared in this scope
jpeg.cpp:506: error: 'jpeg_destroy_compress' was not declared in this scope
jpeg.cpp: In member function 'virtual void jpeg::output_impl::write_scanline(unsigned char*)':
jpeg.cpp:513: error: 'm_cinfo' was not declared in this scope
jpeg.cpp:513: error: 'jpeg_write_scanlines' was not declared in this scope
make[2]: *** [jpeg.lo] Error 1
make[2]: Leaving directory `/home/josh/Desktop/gnash-0.7.1/libbase'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/josh/Desktop/gnash-0.7.1'
make: *** [all] Error 2


But I don't know what it's telling me, why it's not working. Can anyone help me with this?

---

