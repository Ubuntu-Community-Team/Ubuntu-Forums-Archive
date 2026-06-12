---
title: "F-Spot 0.4.2 crashes on importing photos - Ubuntu 8.04"
date: 2008-04-28
forum: General Help
---

### Post by x001 on 2008-04-28
I am using Ubuntu 8.04 with all the updates on Dell XPS1530 and f-spot 0.4.2.
When I first run F-spot it asks me to select the the location to import photos (approximately 3500 photos). During the import (approx. 500 photos in) f-spot just disappears.

I removed the f-spot folder from the .gnome2 folder and tried again but this time starting it through the command line:

```
mono --debug /usr/lib/f-spot/f-spot.exe
```

Output:


```
Syncing metadata to file...
old = "" new = "" heading = "ASCII"
value = 2007:01:31 01:39:12 len = 19
<uuid:faf5bdd5-ba3d-11da-ad31-d33d75182f1b> <http://ns.microsoft.com/photo/1.0DateAcquired> "2007-04-02T03:54:53Z" .
_:bnode1923688448 <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://www.w3.org/1999/02/22-rdf-syntax-ns#Bag> .
_:bnode1923688448 <http://www.w3.org/1999/02/22-rdf-syntax-ns#_1> "Hawaii 2007" .
_:bnode-509834752 <http://ns.microsoft.com/photo/1.0LastKeywordXMP> _:bnode1923688448 .
_:bnode-868477696 <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://www.w3.org/1999/02/22-rdf-syntax-ns#Bag> .
_:bnode-868477696 <http://www.w3.org/1999/02/22-rdf-syntax-ns#li> "Hawaii 2007" .
<http://fakebase.f-spot.org/internal/> <http://purl.org/dc/elements/1.1/subject> _:bnode-868477696 .
<http://fakebase.f-spot.org/internal/> <http://ns.adobe.com/xap/1.0/Rating> "0" .
value = f-spot version 0.4.2 len = 20
value = 2008:04:28 14:45:47 len = 19
value = f-spot version 0.4.2 len = 20
value = 2008:04:28 14:45:47 len = 19
Saved 14405 bytes
System.Xml.XmlException: '1.0DateAcquired' is not a valid XML Name
  at System.Xml.XmlConvert.VerifyName (System.String name) [0x00000] 
  at System.Xml.XmlElement..ctor (System.String prefix, System.String localName, System.String namespaceURI, System.Xml.XmlDocument doc, Boolean atomizedNames) [0x00000] 
  at System.Xml.XmlDocument.CreateElement (System.String prefix, System.String localName, System.String namespaceURI) [0x00000] 
  at System.Xml.XmlDocument.CreateElement (System.String qualifiedName, System.String namespaceURI) [0x00000] 
  at SemWeb.RdfXmlWriter.CreatePredicate (System.Xml.XmlElement subject, SemWeb.Entity predicate) [0x00000] 
  at SemWeb.RdfXmlWriter.Add (Statement statement) [0x00000] 
  at FSpot.Xmp.XmpFile+XmpWriter.Add (Statement stmt) [0x00000] 
  at SemWeb.RdfWriter.SemWeb.StatementSink.Add (Statement statement) [0x00000] 
  at SemWeb.MemoryStore.Select (Statement template, StatementSink result) [0x00000] 
  at SemWeb.Store.Select (StatementSink result) [0x00000] 
  at SemWeb.RdfWriter.Write (StatementSource source) [0x00000] 
  at FSpot.Xmp.XmpFile.Save (System.IO.Stream stream) [0x00000] 
Syncing metadata to file...
old = "" new = "" heading = "ASCII"
value = 2007:01:31 02:06:43 len = 19
<uuid:faf5bdd5-ba3d-11da-ad31-d33d75182f1b> <http://ns.microsoft.com/photo/1.0DateAcquired> "2007-04-02T03:54:53Z" .
_:bnode-1881954560 <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://www.w3.org/1999/02/22-rdf-syntax-ns#Bag> .
_:bnode-1881954560 <http://www.w3.org/1999/02/22-rdf-syntax-ns#_1> "Hawaii 2007" .
_:bnode-20510464 <http://ns.microsoft.com/photo/1.0LastKeywordXMP> _:bnode-1881954560 .
_:bnode-379153408 <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://www.w3.org/1999/02/22-rdf-syntax-ns#Bag> .
_:bnode-379153408 <http://www.w3.org/1999/02/22-rdf-syntax-ns#li> "Hawaii 2007" .
<http://fakebase.f-spot.org/internal/> <http://purl.org/dc/elements/1.1/subject> _:bnode-379153408 .
<http://fakebase.f-spot.org/internal/> <http://ns.adobe.com/xap/1.0/Rating> "0" .
value = f-spot version 0.4.2 len = 20
value = 2008:04:28 14:45:48 len = 19
value = f-spot version 0.4.2 len = 20
value = 2008:04:28 14:45:48 len = 19
Saved 16593 bytes
System.Xml.XmlException: '1.0DateAcquired' is not a valid XML Name
  at System.Xml.XmlConvert.VerifyName (System.String name) [0x00000] 
  at System.Xml.XmlElement..ctor (System.String prefix, System.String localName, System.String namespaceURI, System.Xml.XmlDocument doc, Boolean atomizedNames) [0x00000] 
  at System.Xml.XmlDocument.CreateElement (System.String prefix, System.String localName, System.String namespaceURI) [0x00000] 
  at System.Xml.XmlDocument.CreateElement (System.String qualifiedName, System.String namespaceURI) [0x00000] 
  at SemWeb.RdfXmlWriter.CreatePredicate (System.Xml.XmlElement subject, SemWeb.Entity predicate) [0x00000] 
  at SemWeb.RdfXmlWriter.Add (Statement statement) [0x00000] 
  at FSpot.Xmp.XmpFile+XmpWriter.Add (Statement stmt) [0x00000] 
  at SemWeb.RdfWriter.SemWeb.StatementSink.Add (Statement statement) [0x00000] 
  at SemWeb.MemoryStore.Select (Statement template, StatementSink result) [0x00000] 
  at SemWeb.Store.Select (StatementSink result) [0x00000] 
  at SemWeb.RdfWriter.Write (StatementSource source) [0x00000] 
  at FSpot.Xmp.XmpFile.Save (System.IO.Stream stream) [0x00000] 
Syncing metadata to file...
old = "" new = "" heading = "ASCII"
value = 2007:01:31 21:12:15 len = 19
<uuid:faf5bdd5-ba3d-11da-ad31-d33d75182f1b> <http://ns.microsoft.com/photo/1.0DateAcquired> "2007-04-02T03:54:53Z" .
_:bnode-1532059648 <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://www.w3.org/1999/02/22-rdf-syntax-ns#Bag> .
_:bnode-1532059648 <http://www.w3.org/1999/02/22-rdf-syntax-ns#_1> "Hawaii 2007" .
_:bnode329384448 <http://ns.microsoft.com/photo/1.0LastKeywordXMP> _:bnode-1532059648 .
_:bnode-29258496 <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://www.w3.org/1999/02/22-rdf-syntax-ns#Bag> .
_:bnode-29258496 <http://www.w3.org/1999/02/22-rdf-syntax-ns#li> "Hawaii 2007" .
<http://fakebase.f-spot.org/internal/> <http://purl.org/dc/elements/1.1/subject> _:bnode-29258496 .
<http://fakebase.f-spot.org/internal/> <http://ns.adobe.com/xap/1.0/Rating> "0" .
value = f-spot version 0.4.2 len = 20
value = 2008:04:28 14:45:48 len = 19
value = f-spot version 0.4.2 len = 20
value = 2008:04:28 14:45:48 len = 19
Stacktrace:


Native stacktrace:

	mono [0x816b1fa]
	mono [0x807de81]
	[0xb7f88440]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7ce5940 (LWP 15841)]
[New Thread 0xb2d2fb90 (LWP 15861)]
[New Thread 0xb2e34b90 (LWP 15852)]
[New Thread 0xb3fcab90 (LWP 15851)]
[New Thread 0xb40cfb90 (LWP 15850)]
[New Thread 0xb56cfb90 (LWP 15847)]
[New Thread 0xb727ab90 (LWP 15843)]
[New Thread 0xb729eb90 (LWP 15842)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

0xb5b7a87f in ?? ()
  8 Thread 0xb729eb90 (LWP 15842)  0xb7f88410 in __kernel_vsyscall ()
  7 Thread 0xb727ab90 (LWP 15843)  0xb7f88410 in __kernel_vsyscall ()
  6 Thread 0xb56cfb90 (LWP 15847)  0xb7f88410 in __kernel_vsyscall ()
  5 Thread 0xb40cfb90 (LWP 15850)  0xb7f88410 in __kernel_vsyscall ()
  4 Thread 0xb3fcab90 (LWP 15851)  0xb7f88410 in __kernel_vsyscall ()
  3 Thread 0xb2e34b90 (LWP 15852)  0xb7f88410 in __kernel_vsyscall ()
  2 Thread 0xb2d2fb90 (LWP 15861)  0xb7f88410 in __kernel_vsyscall ()
  1 Thread 0xb7ce5940 (LWP 15841)  0xb5b7a87f in ?? ()

Thread 8 (Thread 0xb729eb90 (LWP 15842)):
#0  0xb7f88410 in __kernel_vsyscall ()
#1  0xb7ea8196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb729e344 in ?? ()
#4  0x00000000 in ?? ()

Thread 7 (Thread 0xb727ab90 (LWP 15843)):
#0  0xb7f88410 in __kernel_vsyscall ()
#1  0xb7ea4aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0xb77781dc in ?? ()
#4  0xb77781c4 in ?? ()
#5  0xb3e577a7 in exif_data_free () from /usr/lib/libexif.so.12
#6  0x0810b3cd in ?? ()
#7  0x00000000 in ?? ()

Thread 6 (Thread 0xb56cfb90 (LWP 15847)):
#0  0xb7f88410 in __kernel_vsyscall ()
#1  0xb7ea4dd2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ba in ?? ()
#3  0xb77787c4 in ?? ()
#4  0xb77787ac in ?? ()
#5  0xb56cf05c in ?? ()
#6  0xb43c2c98 in ?? ()
#7  0xb56cf080 in ?? ()
#8  0xb56cf05c in ?? ()
#9  0xb77787c4 in ?? ()
#10 0x00000490 in ?? ()
#11 0xb7ea58c5 in pthread_getspecific ()
   from /lib/tls/i686/cmov/libpthread.so.0
#12 0x0810b3cd in ?? ()
#13 0x00000001 in ?? ()
#14 0x08109510 in ?? ()
#15 0x00000000 in ?? ()

Thread 5 (Thread 0xb40cfb90 (LWP 15850)):
#0  0xb7f88410 in __kernel_vsyscall ()
#1  0xb7ea4dd2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ba in ?? ()
#3  0xb777f8d4 in ?? ()
#4  0xb777f8bc in ?? ()
#5  0xb40cf064 in ?? ()
#6  0x082057f4 in ?? ()
#7  0xb7e71ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#8  0xb40cf064 in ?? ()
#9  0xb777f8d4 in ?? ()
#10 0xb1700810 in ?? ()
#11 0xb7d94b05 in calloc () from /lib/tls/i686/cmov/libc.so.6
#12 0x0810b3cd in ?? ()
#13 0x00000001 in ?? ()
#14 0x08109510 in ?? ()
#15 0x00000000 in ?? ()

Thread 4 (Thread 0xb3fcab90 (LWP 15851)):
#0  0xb7f88410 in __kernel_vsyscall ()
#1  0xb7ea4dd2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ba in ?? ()
#3  0xb7778b24 in ?? ()
#4  0xb7778b0c in ?? ()
#5  0xb3fca05c in ?? ()
#6  0x00000001 in ?? ()
#7  0xb7f67248 in ?? () from /usr/lib/libglib-2.0.so.0
#8  0xb3fca05c in ?? ()
#9  0xb7778b24 in ?? ()
#10 0x0821b240 in ?? ()
#11 0x08efe378 in ?? ()
#12 0x4816458f in ?? ()
#13 0x36007680 in ?? ()
#14 0x08204ce8 in ?? ()
#15 0x00000001 in ?? ()
#16 0x00000000 in ?? ()

Thread 3 (Thread 0xb2e34b90 (LWP 15852)):
#0  0xb7f88410 in __kernel_vsyscall ()
#1  0xb7ea4dd2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ba in ?? ()
#3  0xb777f940 in ?? ()
#4  0xb777f928 in ?? ()
#5  0xb2e3405c in ?? ()
#6  0xb439e3c0 in ?? ()
#7  0xb7ea2531 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x0810b3cd in ?? ()
#9  0x00000001 in ?? ()
#10 0x08109510 in ?? ()
#11 0x00000000 in ?? ()

Thread 2 (Thread 0xb2d2fb90 (LWP 15861)):
#0  0xb7f88410 in __kernel_vsyscall ()
#1  0xb7df6881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f24e14 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f251dc in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  0xb30c0848 in ?? ()
#6  0xb30c0844 in ?? ()
#7  0xb30c0840 in ?? ()
#8  0xb30c083c in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread 0xb7ce5940 (LWP 15841)):
#0  0xb5b7a87f in ?? ()
#1  0x02b68f00 in ?? ()
#2  0xbfe32160 in ?? ()
#3  0xb5b7a854 in ?? ()
#4  0x02b68f00 in ?? ()
#5  0x02b68f00 in ?? ()
#6  0x00271db0 in ?? ()
#7  0xbfe3219c in ?? ()
#8  0xb2f33383 in ?? ()
#9  0x0003f810 in ?? ()
#10 0x02b68f00 in ?? ()
#11 0x4816539f in ?? ()
#12 0x00000000 in ?? ()
#0  0xb5b7a87f in ?? ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

Any help is appreciated.

---

### Post by TeoBigusGeekus on 2008-04-28
Why don't you try to uninstall and then reinstall f-spot?

---

### Post by x001 on 2008-04-28
Tried uninstall/reinstall already using the Add/Remove application and f-spot still crashes importing photos. Is there something else that I need to do to uninstall/reinstall?

---

### Post by TeoBigusGeekus on 2008-04-28
Try to uninstall through synaptic package manager. In there, choose complete removal of the package.

---

### Post by x001 on 2008-04-28
Just did a complete removal using synaptic package manager and removed the f-spot folder from the .gnome2 director plus the partial Photo folder and reinstalled f-spot. Attempted to import photos and this time it seemed like it got to 700 photos and crashed.

---

### Post by TeoBigusGeekus on 2008-04-28
Not actually a solution, but a practical advice:
Re-uninstall, install and import your photos in folders of 300 photos maximum.

---

### Post by x001 on 2008-04-28
Thanx for helping out.

Ok, tried your recommendation. During the import, selected folder at a time. It crashed on a particular folder that had only 47 images. So I removed the f-spot config/db folder and photos folder. Uninstalled/Reinstalled. Removed the folder that crashed f-spot and tried importing folders one by one and this time it crashed on a different folder the only had 5 photos. Removed the folder and attempted the same process again and f-spot crashed again on a different folder the only had 30 photos. So it seems like this is random.

I have Ubuntu 8.04 installed on my desktop (Dell XPS410) and F-spot imported all the photos without any problems. I am attemtping to import the same photos on my laptop.

---

### Post by x001 on 2008-04-28
Backed up my data to an external usb hd and reinstalled Ubuntu 8.04.
After reinstall made sure there were no new updates then attempted to import photos via f-spot. It was successful.

I think the update from beta to production might have caused the issue.

Thanx for helping out.

---

### Post by hariprs on 2008-04-28
I am also facing this problem. When i tried to import photos from my cannon camera it crashed and never opens again. I tried uninstall/install but no use.

---

### Post by x001 on 2008-04-28
I would try removing (or renaming if you want to keep the photos database) the f-spot folder from the .gnome2 directory.

/home/username/.gnome2/f-spot

Open your home folder and press Ctrl + H to view hidden folders. Locate .gnome2 and open it. Rename/move/or delete the f-spot directory then restart F-spot.

---

### Post by cetheriel on 2008-12-11
i'm using 0.4.3.1 on hardy, issue is still up.

---

