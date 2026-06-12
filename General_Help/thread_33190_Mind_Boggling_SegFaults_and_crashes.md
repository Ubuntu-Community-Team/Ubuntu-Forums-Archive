---
title: "Mind Boggling SegFaults and crashes"
date: 2005-05-09
forum: General Help
---

### Post by willistg on 2005-05-09
Hello,

First of all, I'm loving ubuntu. so thanks for making it.

Now my problem...

I'm experiencing some issues with the system freezing up occasionally. Normally I don't consider this a big deal. But I'm getting it consitently enough on certain activities.

When ripping a cd, I have yet to get a sucessful rip of a cd. I've tried many cd's many rippers(grip,jack). Always the same thing.

The computer stops responding(I can't even ssh in from another computer), usually 80% of the way through it.

So, here's what I've checked so far.

I've turned dma on and off with no change. I've tried the stock kernel and the one for amd(k7).

I went a bit further to try and diagnose the problem. and here's what I found.

I can rip the data from audio cds sucessfully. I can not get through encoding an entire cd(I got close though 8 out of 9 tracks).

So I tried both oggenc and lame both have the same behavior which is one of 2 things.

They either segfault with no other information available, or cause te computer to stop responding. 

I think it maybe library or hardware config related because a lot of write operations to disk have not locked it up yet.

my test script to for the problem is this...

```

for file in *.wav; 
	do
		echo "processing $file"; 
		oggenc -q 5 -f - < $file > /dev/null; 
	done

```

I thought if I just piped to /dev/null I'd remove the possibility of disk writes causing the problem. Imay be way off base here, I have no knowledge of the inner workings of oggenc, or lame.

Anywho, I'm hoping someone more poweruserish can point me in the right direction for what I could do next to further isolate the problem.

one last thing...

both lame and oggenc share some lib dependecies. If I knew how to turn on debugging or attach a debugger I would.

```

twillis@tomspc:~$ ldd /usr/bin/lame
                libncurses.so.5 => /lib/libncurses.so.5 (0xb7fa0000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f7f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e52000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0xb7feb000)
twillis@tomspc:~$ ldd /usr/bin/oggenc
                libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb7ef5000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb7ece000)
        libOggFLAC.so.1 => /usr/lib/libOggFLAC.so.1 (0xb7ebc000)
        libFLAC.so.6 => /usr/lib/libFLAC.so.6 (0xb7e87000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e66000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb7e61000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d34000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0xb7feb000)
twillis@tomspc:~$


```

 ](*,)

thanks for your time


Tom Willis

---

### Post by willistg on 2005-05-12
WOW!!! I overthought this thing by a mile.

Bad ram was the cause it seems according to memtest([http://www.memtest.org](http://www.memtest.org)) so I'm off to the puter store for some new ram. It would have been nice to learn how to debug etc..... but perhaps another time.



Tom

---

### Post by shakin on 2005-05-12
[QUOTE=willistg]WOW!!! I overthought this thing by a mile.

Bad ram was the cause it seems according to memtest([http://www.memtest.org](http://www.memtest.org)) so I'm off to the puter store for some new ram. It would have been nice to learn how to debug etc..... but perhaps another time.

Tom[/QUOTE]

LOL, I was just going to say maybe you have bad RAM. Too bad I didn't read this thread earlier. My diagnosis was simply that "odd problems == bad ram" in most cases. This would be especially true for memory intensive programs like audio encoding. Diagnosing bad RAM is very difficult unless you run memtest. I once had a bad stick that made it impossible to install Windows 98. Install would crap out half way through. Since I had just bought a new hard drive I thought that was the problem. Even a tech guy at a computer shop said it was a bad hard drive. Doh!

I was also going to ask if you had installed any libraries from a non-official repository, but I'm glad you didn't because it's easier to fix a bad RAM problem.

---

### Post by willistg on 2005-05-12
[QUOTE=shakin]LOL, I was just going to say maybe you have bad RAM. Too bad I didn't read this thread earlier. My diagnosis was simply that "odd problems == bad ram" in most cases. This would be especially true for memory intensive programs like audio encoding. Diagnosing bad RAM is very difficult unless you run memtest. I once had a bad stick that made it impossible to install Windows 98. Install would crap out half way through. Since I had just bought a new hard drive I thought that was the problem. Even a tech guy at a computer shop said it was a bad hard drive. Doh!

I was also going to ask if you had installed any libraries from a non-official repository, but I'm glad you didn't because it's easier to fix a bad RAM problem.[/QUOTE]
 Yeah I don't know what's wrong with me. I develop on windows for my "real" job and my troubleshooting skills usually starts with getting the hardware out of the way as a variable, but darned if I just lose my mind when I'm sitting in front of my linux box. I guess since it's so vastly different to windows(in my head) I figure I need to learn new rules.

I need to pick some gurus brain for some of this troubleshooting stuff. :lol:

Anyway, new batch of ram confirmed good to go by memtest, no longer locking up in my tests(a good thing) but sometimes freezing up in xorg when I'm doing several things at once. I think this is a different problem so i'm going snooping and If I can't figure out anything I'll start ranting on linux msgboards again. :)

---

