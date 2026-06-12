---
title: "problems with ktorrent!!"
date: 2007-10-13
forum: General Help
---

### Post by roy92 on 2007-10-13
I open KTorrent and it says "You are already downloading this torrent ......... the list of trackers of both torrents has been merged. it appears 2 times. Then I open it  and it says that it cant be downloaded because Error: Cannot open /home/roger/.kde/share/apps/ktorrent/tor0/cache/ : is a directory.

I remove the torrent  and it ask me if i want to remove the incomplete data, I say yes and it crash the backtrace says: 

  
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb712aae9 in QString::setLength () from /usr/lib/libqt-mt.so.3
#7  0xb712ac0e in QString::grow () from /usr/lib/libqt-mt.so.3
#8  0xb712ba21 in QString::operator+= () from /usr/lib/libqt-mt.so.3
#9  0xb7d9fa48 in bt::MultiFileCache::deleteDataFiles ()
   from /usr/lib/libktorrent-2.1.so
#10 0xb7d6a9c4 in bt::ChunkManager::deleteDataFiles ()
   from /usr/lib/libktorrent-2.1.so
#11 0xb7d7fb43 in bt::TorrentControl::deleteDataFiles ()
   from /usr/lib/libktorrent-2.1.so
#12 0x080791b5 in ?? ()
#13 0x0807b590 in ?? ()
#14 0xb6e1088b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#15 0x0806c840 in ?? ()
#16 0x080706c8 in ?? ()
#17 0x08065d3d in ?? ()
#18 0x0806abc9 in ?? ()
#19 0xb6e1088b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#20 0xb6e11330 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#21 0xb775b4c9 in KAction::activated () from /usr/lib/libkdeui.so.4
#22 0xb7793cc2 in KAction::slotActivated () from /usr/lib/libkdeui.so.4
#23 0xb7793c5c in KAction::slotButtonClicked () from /usr/lib/libkdeui.so.4
#24 0xb7861356 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#25 0xb6e1088b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#26 0xb7790970 in KToolBarButton::buttonClicked () from /usr/lib/libkdeui.so.4
#27 0xb7790c76 in KToolBarButton::mouseReleaseEvent ()
   from /usr/lib/libkdeui.so.4
#28 0xb6e4765d in QWidget::event () from /usr/lib/libqt-mt.so.3
#29 0xb780c9a1 in KToolBarButton::event () from /usr/lib/libkdeui.so.4
#30 0xb6da7a60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#31 0xb6da9c1e in QApplication::notify () from /usr/lib/libqt-mt.so.3
#32 0xb756bcc2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#33 0xb6d3a25d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#34 0xb6d38ec2 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3

Then i open it again and it says: Several data files of the torrent "........................" are missing, do you want to recreate them, or do you want to not download them?

And it choose recreate and ktorrent get stuck, and if i choose not download is the same thing of the errors...

---

### Post by 001100 on 2007-10-14
use azureus. I used ktorrent and azureus downloads faster and works better

---

### Post by milosz.galazka on 2007-10-14
I am using ktorrent and I can't say anything bad about it...
It's very good bittorrent client.

Try to move */home/roger/.kde/share/apps/ktorrent/tor0* directory elsewhere and start ktorrent and if everything is fine you could delete it or whatever...

---

