---
title: "kplayer / mplayer"
date: 2005-09-23
forum: General Help
---

### Post by geearf on 2005-09-23
Hello,

to obtain fullscreen and good speed with mplayer, I had to install svgalibhelper and so on to access VIDIX without needing any root / sudo, and now it works flawlessly.

But now I cannot access xvidix in kplayer (when I start a video I just get the error / inactif text at the bottom), and therefore I cannot really use it, cause the rest is very slow on my laptop.

If anyone has an idea on this I'll be pleased

---

### Post by npu on 2005-12-28
[QUOTE=geearf]to obtain fullscreen and good speed with mplayer, I had to install svgalibhelper and so on to access VIDIX without needing any root / sudo, and now it works flawlessly.[/QUOTE]Can you please give me a link on how to do that?

Since I installed drivers for my video card (ATI Radeon 9200se) Mplayer has problems playing videos. vo=xv doesn't work, vo=x11 gives me slow motion in full screen. And vo=xvidix:radeon_vid.so requires root privileges (which is annoying/stupid). I dunno what to do. Google/UForum search hasn't helped.

It makes no sense to me how installing video drivers actually makes the computer _less_ capable of playing video.

---

### Post by geearf on 2005-12-29
Hello,

here is a link : 
[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#vidix](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#vidix)

If you have any trouble (I had a lot, but I don't remember for what exactly), I still have the directory needed to compile.

---

### Post by npu on 2005-12-29
Well, I'm stuck at section #2 of the doc's guide.

```
$ make
grep: /lib/modules/2.6.12-10-k7/build/include/linux/device.h: No such file or directory
make -C /lib/modules/2.6.12-10-k7/build SUBDIRS=/foo/svgalib_helper CLASS_CFLAGS= modules
make: *** /lib/modules/2.6.12-10-k7/build: No such file or directory.  Stop.
make: *** [default] Error 2
```

---

### Post by geearf on 2005-12-29
you need to have the sources or the headers of your kernel to compile a kernel module.

---

### Post by npu on 2005-12-29
Thanks for helping.

I did part 1-5 with no problems. But when trying to compile libdha as described in #6 ("make" in the mplayer/libdha/ dir), it tells me: "make: `libdha.so.1.0' is up to date". Since this a fresh Mplayer install from source, and svgalib_helper/ was added to the libdha directory after compiling Mplayer I don't see why it says it's up to date (by the way, the CFLAGS-line in Makefile is uncommented).

Actually I slipped and did:
```
$ sudo make install
mkdir -p /usr/local/lib
install -m 755 -s -p libdha.so.1.0  /usr/local/lib/libdha.so.1.0
rm -f /usr/local/lib/libdha.so
ln -sf libdha.so.1.0  /usr/local/lib/libdha.so.1
ldconfig
```
And so I tried running Mplayer:
```
$ mplayer foo.avi
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

vidixlib: dlopen error: libdha.so.1.0: cannot open shared object file: No such file or directory
vosub_vidix: Couldn't find working VIDIX driver
```The files /usr/local/lib/libdha.so.1 and /usr/local/lib/libdha.so.1.0 exist. I'm pretty sure the make install and trying Mplayer is going one step too far, but what have I done wrong?

---

### Post by geearf on 2005-12-29
you need to make install libdha also, but before doing any make in there, you need to copy the svgalib_helper directory in the libdha directory.
Then make, make install / checkinstall (I do that).
Then you need to modprobe the svgalib_helper module, and to start I don't know which script (I've put the lines in /etc/init.d/bootmisc.sh).

---

### Post by geearf on 2005-12-29
locate libdha.so
/usr/lib/libdha.so.1.0
/usr/lib/libdha.so
/usr/local/lib/libdha.so.1
/usr/local/lib/libdha.so.1.0

I can't tell you which one is the right one, but I do remember having some problems there too.

---

### Post by npu on 2005-12-29
[QUOTE=geearf]you need to make install libdha also, but before doing any make in there, you need to copy the svgalib_helper directory in the libdha directory.[/QUOTE]Yes, this is exactly what I did (as described in my last post, sorry if I wasn't clear enough).

> Then you need to modprobe the svgalib_helper module, and to start I don't know which script (I've put the lines in /etc/init.d/bootmisc.sh).Ok. Any help appreciated on doing that. :) 

Weird. "locate libdha.so" gives me nothing, even though libdha.so.1 and libdha.so.1.0 are placed in /usr/local/lib/.

---

### Post by geearf on 2005-12-30
1- sorry my fault, I was too tired :)

2- you can try sudo updatedb and then the locate in case the database is too old.

---

### Post by npu on 2005-12-30
It works! :D 

I had to copy them ("sudo cp /usr/local/lib/libdha.so* /usr/lib/" for future reference) and after an "updatedb" mplayer now works perfectly with vo="xvidix:radeon_vid.so".

I thought I was gonna fail on making this work... Thanks SO much for your help, geearf!

---

### Post by geearf on 2005-12-30
My pleasure,

just beware of a problem I had with xvidi (not using it anymore because of that), with newest ati driver, when I'm 'trying' to watch a video, the video will be full of crap, and not watchable at all, so I reverted to xv for this.

---

### Post by npu on 2005-12-31
[QUOTE=geearf]My pleasure,

just beware of a problem I had with xvidi (not using it anymore because of that), with newest ati driver, when I'm 'trying' to watch a video, the video will be full of crap, and not watchable at all, so I reverted to xv for this.[/QUOTE]Ok, sorry to hear that. I can't use xv at all. Bu the way, concerning your kplayer issue, I had the same problems.

But... Something really weird has happened here. Suddenly my Mplayer can't play videos anymore. I haven't changed anything in my setup, all I did was reboot my computer today (did some computer vacuuming). I get this:

```
$ mplayer foo.avi
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

[radeon] Error occurred during pci scan: Operation not permitted
vosub_vidix: Couldn't find working VIDIX driver
```
and:

```
$ sudo mplayer foo.avi
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

[radeon] Can't find chip
vosub_vidix: Couldn't find working VIDIX driver
```
Can't find chip? My xorg.conf looks fine. Concerning the libs locate gives me:

```
$ locate libdha.so
/usr/lib/libdha.so.1
/usr/lib/libdha.so.1.0
/usr/local/lib/libdha.so.1.0
/usr/local/lib/libdha.so.1
```
This is really getting on my nerves... Anyone have any ideas?

(Edit: Just for reference, I have a ~/.mplayer/config file with the line 'vo="xvidix:radeon_vid.so"' in it. Running with -vo xv doesn't work, -vo x11 is still slow motion in fullscreen. Sigh.)

---

### Post by geearf on 2006-01-01
it's because of the "make device" thing.
I told I have put some lines in /etc/init.d/bootmisc.sh, well I guess it must be this :)

Try remaking "make device" and see if it works, if yes you need to do so every time you reboot, I choosed the bootmisc.sh but you can do something else :)

---

### Post by npu on 2006-01-01
Ah, so there's still hope. Thanks for hanging in there with me on this. :)

"make device" does not work. It is stated in the guide:
>  To create the necessary devices in the /dev  directory, do a
make device
**in the svgalib_helper dir**, as root....and that is a few steps **before** the guide is "finished". You said something about modprobe, could you specify what you do/did?

---

### Post by geearf on 2006-01-02
put svgalib_helper in your /etc/modules

---

### Post by geearf on 2006-01-02
just to say that I've just tried cvidix without X, it's pretty fun on my laptop with an ati, but on my desktop, I don't see any video :(

---

### Post by npu on 2006-01-02
Perhaps I'm really stupid, but I don't understand this at all...

I put the line "svgalib_helper" in /etc/modules. That doesn't help.

I have no svgalib_helper directory (except for the one in the libdha _source_ directory which I still have left). If I run "make device" from there I get:

```
$ sudo make device
Password:
rm -f /dev/svga /dev/svga?
mknod -m 666 /dev/svga c 209 0
mknod -m 666 /dev/svga1 c 209 1
mknod -m 666 /dev/svga2 c 209 2
mknod -m 666 /dev/svga3 c 209 3
mknod -m 666 /dev/svga4 c 209 4
```
Still the same error messages in Mplayer (No permissions / no chip)

---

### Post by geearf on 2006-01-03
I put the line "svgalib_helper" in /etc/modules. That doesn't help.
>> you need to reboot, or for the instance to do modprobe svgalib_helper

rm -f /dev/svga /dev/svga?
mknod -m 666 /dev/svga c 209 0
mknod -m 666 /dev/svga1 c 209 1
mknod -m 666 /dev/svga2 c 209 2
mknod -m 666 /dev/svga3 c 209 3
mknod -m 666 /dev/svga4 c 209 4

>> this is needed, but only after the module has been loaded.

You can still try to start mplayer with sudo to see if you have vidix and miss the permission or if vidix itselft does not work also.

---

### Post by npu on 2006-01-03
Hmm, modprobe gives me:
```
$ modprobe svgalib_helper
FATAL: Module svgalib_helper not found.
```
> you need to reboot, or for the instance to do modprobe svgalib_helper
Reboot doesn't help.

> You can still try to start mplayer with sudo to see if you have vidix and miss the permission or if vidix itselft does not work also.
Running Mplayer as sudo doesn't help (same error message as the one I posted this Sunday, i.e. Can't find chip).

I'm seriously thinking of giving this up. Sad but true.

---

### Post by geearf on 2006-01-03
During the compilation of the svgalib_helper you should have copied the .ko file to a place from which you can modprobe it (or use it from /etc/modules), but this only help if you can already use mplayer with sudo, if not then you have a vidix problem.

Hhmm, maybe you should try specifying the vidix driver to use in the command line, and post me a bigger output for more help on it.

---

### Post by geearf on 2006-01-21
so,no news from you anymore ?

I've just installed vidix on my desktop quite easily (well now that I know of some tricks ..).

---

