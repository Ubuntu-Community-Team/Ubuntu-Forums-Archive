---
title: "Akregator crashing in Kubuntu"
date: 2007-12-14
forum: General Help
---

### Post by Tekno_Cowboy on 2007-12-14
I'm having the trouble of akregator crashing on me. I get a Signal 11 (SIGSEGV) and the following backtrace

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
[New Thread -1243556160 (LWP 6614)]
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
#6  0xb5eb0cbc in memcpy () from /lib/tls/i686/cmov/libc.so.6
#7  0xb58e1483 in c4_String::Init ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#8  0xb58d8003 in c4_HandlerSeq::Prepare ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#9  0xb58dbb70 in c4_Persist::LoadAll ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#10 0xb58e08cd in c4_Storage::c4_Storage ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#11 0xb58c4686 in Akregator::Backend::FeedStorageMK4Impl::FeedStorageMK4Impl
    () from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#12 0xb58c6aa1 in Akregator::Backend::StorageMK4Impl::archiveFor ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#13 0xb7f33ad1 in Akregator::Feed::loadArticles ()
   from /usr/lib/libakregatorprivate.so
#14 0xb7f34840 in Akregator::Feed::fromOPML ()
   from /usr/lib/libakregatorprivate.so
#15 0xb7f3f0a5 in Akregator::FeedList::parseChildNodes ()
   from /usr/lib/libakregatorprivate.so
#16 0xb7f3f61e in Akregator::FeedList::readFromXML ()
   from /usr/lib/libakregatorprivate.so
#17 0xb5aa322c in Akregator::View::loadFeeds ()
   from /usr/lib/kde3/libakregatorpart.so
#18 0xb5aa018b in Akregator::Part::openFile ()
   from /usr/lib/kde3/libakregatorpart.so
#19 0xb5a9c4cc in Akregator::Part::openURL ()
   from /usr/lib/kde3/libakregatorpart.so
#20 0xb5a981db in Akregator::Part::openStandardFeedList ()
   from /usr/lib/kde3/libakregatorpart.so
#21 0xb5aaee70 in Akregator::AkregatorPartIface::process ()
   from /usr/lib/kde3/libakregatorpart.so
#22 0xb6c2b0d7 in DCOPClient::receive () from /usr/lib/libDCOP.so.4
#23 0xb6c2b862 in DCOPClient::send () from /usr/lib/libDCOP.so.4
#24 0xb6c2be9f in DCOPRef::sendInternal () from /usr/lib/libDCOP.so.4
#25 0x08051396 in ?? ()
#26 0xbfde2440 in ?? ()
#27 0xbfde2494 in ?? ()
#28 0xbfde24b4 in ?? ()
#29 0xbfde2474 in ?? ()
#30 0x08063ad8 in ?? ()
#31 0xb7fad660 in ?? () from /lib/ld-linux.so.2
#32 0x08063b08 in ?? ()
#33 0x08055be8 in vtable for QCString ()
#34 0x0806b710 in ?? ()
#35 0x00000000 in ?? ()

```

Could someone please help me?

---

### Post by Tekno_Cowboy on 2007-12-17
I'll ask again, could someone please help me?

---

### Post by Tekno_Cowboy on 2007-12-22
I've been browsing the forums for 6 days now, and have not found an answer to my problem yet. Could someone please at least point me in the right direction?

---

