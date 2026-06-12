---
title: "Feisty as a mad dog :: libthread ... what?"
date: 2007-06-12
forum: General Help
---

### Post by jalfan on 2007-06-12
Hello, 

I am new to Ubuntu and am learning LOTS more about linux than I thought possible.  (My windows crashed and I finnaly gave in).

Well, I've been downloading libraries and all sorts of stuff with this apt-get thinggy.. realllly nice program... mostly for media content (i.e. so I can play .wmv files and streaming video .m4v, etc)

Well I am also interested in RSS and found this neat program called kitty, which after looking into doesn't look like the designer has time to work on it anymore.

The program keeps crashing (at random places) and it wasn't soo much a problem but then konqueror crased also.

They both gave off the sig 11 SIGSEGV and had a backtrace similar to the following:

This is from kitty: (konqueror had similar output save the last few lines)
```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1238476576 (LWP 19529)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb6a97f9a in QShared::deref () from /usr/lib/libqt-mt.so.3
#7  0xb6e8989a in QString::deref () from /usr/lib/libqt-mt.so.3
#8  0xb6e8a69e in QString::operator= () from /usr/lib/libqt-mt.so.3
#9  0x0805d6b2 in ?? ()
#10 0xb6104548 in ?? ()
#11 0xbf87da38 in ?? ()
#12 0xbf87da6c in ?? ()
#13 0x00000000 in ?? ()

```

I can repeat the problem in kitty, 
and please don't judge me on the 
following.. we are all curious at some point in time:

To open kitty:
```

jalfan@asgard:~$ kitty
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Then I did the following:
```

From the menu bar I select  FEED/NekoTongue

Click on NEXT then type in professor p's panorama 
(I originnaly did a different search but due to  
forum regulations I left those word(s) out and 
made sure you could find the result that gave me a problem).

Click NEXT again and wait for search results to load.

Click on Tune In next to professor p's panorama.

Click OK on the Dialog that pops up and you will get your error.

```

I have also received the error when switching between feeds that I was able to subscribe to on the Feeds Panel on the left of the main window.

I don't remember what I was doing when Konqueror crashed but it gave me that same libthread_db.so thingggy.

Thanks for any help anyone can give.

TTFN

---

### Post by jalfan on 2007-06-12
Well, it happened again in Konqueror.  I have it set up to use Kaffeine as the media player for mp3's and mv4's.  I was listening to an mp3 from an RSS feed that I have in Akregator (I have it set up to open a new browser window when a link is clicked and it opens konqueror).

I got tired of listening to the mp3 and closed konqueror and this is the backtrace of what I got:

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233098528 (LWP 21484)]
[New Thread -1252058224 (LWP 21490)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb683d460 in pthread_mutex_lock ()
   from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7d5af26 in pthread_mutex_lock () from /lib/tls/i686/cmov/libc.so.6
#8  0xb6e0f5ef in ?? () from /usr/lib/libX11.so.6
#9  0x00000007 in ?? ()
#10 0xb6ed2b2c in ?? () from /usr/lib/libX11.so.6
#11 0xbfbbe628 in ?? ()
#12 0xb6e274de in XrmQGetResource () from /usr/lib/libX11.so.6
Backtrace stopped: frame did not save the PC

```

Thanks in advance.

---

