---
title: "krita crashes before opening"
date: 2008-05-12
forum: General Help
---

### Post by blairm on 2008-05-12
Hi,

Heard good things about Krita so decided to install it... but it crashes every time before it will open!
This happens on Ubuntu 7.10 and Kubuntu 7.10. Installed it from the repositories via Synaptic.
Have included the error back-trace thing... as you an probably tell from the terminology I use, I'm not exactly a programming wizard:)

Backtrace (have removed all the (no debugging symbols found) lines, since there are heaps of them):

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232602928 (LWP 31439)]
(no debugging symbols found)
...
(no debugging symbols found)
[KCrash handler]
#6  0xb73c6a4b in QScrollView::viewport () from /usr/lib/libqt-mt.so.3
#7  0xb60bc7ca in SqueezedComboBox::SqueezedComboBox ()
   from /usr/lib/libkritaui.so.1
#8  0xb60d542b in WdgNewImage::WdgNewImage () from /usr/lib/libkritaui.so.1
#9  0xb60a6dfc in KisCustomImageWidget::KisCustomImageWidget ()
   from /usr/lib/libkritaui.so.1
#10 0xb60282bd in KisDoc::createCustomDocumentWidget ()
   from /usr/lib/libkritaui.so.1
#11 0xb66e64b1 in KoDocument::createOpenPane ()
   from /usr/lib/libkofficecore.so.3
#12 0xb66e69db in KoDocument::showStartUpWidget ()
   from /usr/lib/libkofficecore.so.3
#13 0xb66ed557 in KoApplication::start () from /usr/lib/libkofficecore.so.3
#14 0xb7fbf06c in kdemain () from /usr/lib/libkdeinit_krita.so
#15 0xb7fc1454 in kdeinitmain () from /usr/lib/kde3/krita.so
#16 0x0804e67f in ?? ()
#17 0x00000001 in ?? ()
#18 0x080a3038 in ?? ()
#19 0x00000001 in ?? ()
#20 0x00000000 in ?? ()



Any ideas would be welcomed.

Cheers,

Blair

---

