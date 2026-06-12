---
title: "Getting started with udftools"
date: 2005-07-27
forum: General Help
---

### Post by Levander on 2005-07-27
Okay, am working on a backup strategy for my Hoary box..  Apparently, I need the udftools package to be able to keep writing to a DVD-RW.

Problem is, I'm having trouble getting started with the udftools package.

The README.Debian file in that package says that UDF support, but not packet writing support is enabled in the 2.6.9 kernel.  And, if you want packet writing support.  You need to patch the kernel.  What exactly is packet writing support?  Has this patch already been applied to the hoary 2.6.9 kernel?

I think I need packet writing support, because it looks like you're supposed to mount your dvd disk via some /dev/pkt??? file onto a directory.  Then, after you've created that device file, you can mount your DVD-RW on your filesystem, and use it like a regular disk partition?

---

### Post by Levander on 2005-07-28
Okay, so I've made a little progress.  Apparently, you have to edit /etc/default/udftools.  Then, when you run 'dpkg-reconfigure udftools', some /dev/pktcdvd/* files get created.  From what I've read, I'm guessing these are the device files used for packet writing.  This step is good, because I believe it means my kernel does have  packet writing support compiled in.  I believe this because of the last section in the README.Debian included with the udftools package.

However, I still can't create a filesystem on a cdrw in the drive. Here are my attempts:

```

levander@bread:/usr/share/doc/udftools $ cdrwtool -d /dev/hdc -q
using device /dev/hdc
1088KB internal buffer
setting write speed to 12x
wait_cmd: Operation not permitted
Command failed: bb 00 ff ff 08 40 00 00 00 00 00 00 - sense 00.00.00
set speed
can't unlock door

levander@bread:/usr/share/doc/udftools $ cdrwtool -d /dev/pktcdvd/0 -q
using device /dev/pktcdvd/0
set_options
can't unlock door

levander@bread:/usr/share/doc/udftools $ mkudffs --media-type=cdrw /dev/hdc
trying to change type of multiple extents

levander@bread:/usr/share/doc/udftools $ mkudffs --media-type=cdrw /dev/pktcdvd/0
trying to change type of multiple extents


```

No idea what I'm doing wrong.

---

### Post by Levander on 2005-07-28
In the output of that first cdrwtool command above.  It says "setting speed to 12x".  Don't know why it's set there.  The drive supports writing to CDRW's at 24x, and the disc itself in the drive only supports 10x.

Could that be causing the "can't unlock door message"?

How do I change the write speed?

---

