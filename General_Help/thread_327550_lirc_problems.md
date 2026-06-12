---
title: "lirc problems"
date: 2006-12-29
forum: General Help
---

### Post by robdeweese on 2006-12-29
Im trying to install lirc from source. It compiles with no errors, but when I go to load the modules I get these errors:

WARNING: Error inserting lirc_dev (/lib/modules/2.6.15-27-386/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_i2c (/lib/modules/2.6.15-27-386/misc/lirc_i2c.ko): Invalid module format

When I run dmesg I get this:

[17183759.864000] lirc_dev: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17183759.864000] lirc_i2c: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17183933.068000] lirc_dev: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17183933.072000] lirc_i2c: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17184038.680000] lirc_dev: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17184038.680000] lirc_i2c: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17184212.912000] lirc_dev: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17184212.912000] lirc_i2c: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17184466.564000] lirc_dev: no version for "struct_module" found: kernel tainted.
[17184466.564000] lirc_dev: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'
[17184466.564000] lirc_i2c: version magic '2.6.15-27-386 preempt 486 gcc-3.4' should be '2.6.15-27-386 preempt 486 gcc-4.0'

I've been at it for hours, can anybody point me in the right direction?

---

### Post by RazorJack on 2006-12-31
Give this a gander:
[http://dyn.yoderhome.com:8080/e/blog/computitude/myth_lirc_debian.writeback](http://dyn.yoderhome.com:8080/e/blog/computitude/myth_lirc_debian.writeback)

Looks like your compiling with the wrong version of GCC.

---

