---
title: "Kubuntu After kde 3.5.5 update Kopete Crashes"
date: 2006-10-14
forum: General Help
---

### Post by SniperZero on 2006-10-14
MODERATORS: Please move to the Installations & upgrades thread.


Well I recently updated to KDE 3.5.5 and it updated Kopete to 0.12.3 (prev version I had was 0.11.3)

When ever I login with my account on Kopete (msn account) it crashes just after the contact list is loaded. If I start Kopete again it crashes I remove ~/.kde/share/apps/kopete and ~/.kde/share/config/kopeterc and it loads up again. If i login with another msn it works fine just until I login with the main msn account I use it crashes.

Console output:
```
kabc: StdAddressBook::self()
kresources: Factory::self()
kio (KSycoca): Trying to open ksycoca from /var/tmp/kdecache-sniperzero/ksycoca
kio (KTrader): query for KResources/Plugin : returning 11 offers
kresources: ManagerImpl::ManagerImpl()
kresources: Connecting DCOP signals...
kresources: ManagerImpl::readConfig()
kresources: Factory::self()
kresources: ManagerImpl::readResourceConfig() kbMYBreNeW
kresources: Factory::resource( file, config )
kio (KDirWatch): Available methods: Stat, FAM, DNotify
kabc: FormatFactory::self()
kio (KDirWatch): Added File /home/sniperzero/.kde/share/apps/kabc/std.vcf [KDirWatch-1]
kio (KDirWatch):  Setup FAM (Req 1) for /home/sniperzero/.kde/share/apps/kabc/std.vcf
kio (KDirWatch): KDirWatch-1 restarted scanning /home/sniperzero/.kde/share/apps/kabc/std.vcf (now 1 watchers)
kabc: StdAddressBook::StdAddressBook()
kresources: Opening resource resource
kopete: File size is zero. Evaluating backups
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__0 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__1 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__2 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__3 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__4 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__5 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__6 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__7 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__8 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__9 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__10 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__11 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__12 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__13 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__14 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__15 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__16 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__17 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__18 size: 0
kopete: Evaluating/home/sniperzero/.kde/share/apps/kabc/std.vcf__19 size: 0
kresources: ManagerImpl::writeConfig()
kresources: Saving resource kbMYBreNeW
kresources: Resource::writeConfig()
kresources: Saving general info
kresources: ManagerImpl::save() finished
kabc: AddressBook::load()
kabc: ResourceFile::load(): '/home/sniperzero/.kde/share/apps/kabc/std.vcf'
kio (KTrader): query for Kopete/Plugin : returning 26 offers
sniperzero@serverbox:~$ kio (KTrader): query for Kopete/Plugin : returning 1 offers
kutils (KSettings::Dispatcher): [static KSettings::Dispatcher* KSettings::Dispatcher::self()]
kutils (KSettings::Dispatcher): [KSettings::Dispatcher::Dispatcher(QObject*, const char*)]
kutils (KSettings::Dispatcher): [void KSettings::Dispatcher::registerInstance(KInstance*, QObject*, const char*)] kopete_msn
kutils (KPluginInfo): [virtual void KPluginInfo::setPluginEnabled(bool)]
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = kopete path = <unknown> pid = 8715
```


Backtrace from KDE crash handler
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
[Thread debugging using libthread_db enabled]
[New Thread -1240684864 (LWP 8715)]
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
#6  0xb6158926 in free () from /lib/tls/i686/cmov/libc.so.6
#7  0xb615a411 in malloc () from /lib/tls/i686/cmov/libc.so.6
#8  0xb64a910b in FcPatternInsertElt () from /usr/lib/libfontconfig.so.1
#9  0xb64a91e6 in FcPatternAddWithBinding () from /usr/lib/libfontconfig.so.1
#10 0xb64a93c7 in FcPatternAdd () from /usr/lib/libfontconfig.so.1
#11 0xb64a9801 in FcPatternAddString () from /usr/lib/libfontconfig.so.1
#12 0xb689804d in QFontDatabase::families () from /usr/lib/libqt-mt.so.3
#13 0xb6899188 in QFontDatabase::findFont () from /usr/lib/libqt-mt.so.3
#14 0xb6814908 in QFontPrivate::load () from /usr/lib/libqt-mt.so.3
#15 0xb6815ca0 in QFontPrivate::engineForScript () from /usr/lib/libqt-mt.so.3
#16 0xb688a9fd in QFontMetrics::width () from /usr/lib/libqt-mt.so.3
#17 0xb7ef99bb in Kopete::UI::ListView::TextComponent::widthForHeight ()
   from /usr/lib/libkopete.so.1
#18 0xb7efb531 in Kopete::UI::ListView::BoxComponent::widthForHeight ()
   from /usr/lib/libkopete.so.1
#19 0xb7efb016 in Kopete::UI::ListView::BoxComponent::layout ()
   from /usr/lib/libkopete.so.1
#20 0xb7efb96b in Kopete::UI::ListView::Item::slotLayoutItems ()
   from /usr/lib/libkopete.so.1
#21 0xb7efbacb in Kopete::UI::ListView::Item::setup ()
   from /usr/lib/libkopete.so.1
#22 0xb69c9b46 in QListViewItem::totalHeight () from /usr/lib/libqt-mt.so.3
#23 0xb69c9bab in QListViewItem::totalHeight () from /usr/lib/libqt-mt.so.3
#24 0xb69c9bab in QListViewItem::totalHeight () from /usr/lib/libqt-mt.so.3
#25 0xb69ceeab in QListView::buildDrawableList () from /usr/lib/libqt-mt.so.3
#26 0xb69d17d4 in QListView::drawContentsOffset () from /usr/lib/libqt-mt.so.3
#27 0xb6a0c1ce in QScrollView::viewportPaintEvent ()
   from /usr/lib/libqt-mt.so.3
#28 0xb72419a8 in KListView::viewportPaintEvent () from /usr/lib/libkdeui.so.4
#29 0xb6a0efce in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#30 0xb69d36ed in QListView::eventFilter () from /usr/lib/libqt-mt.so.3
#31 0xb7ef81f6 in Kopete::UI::ListView::ListView::eventFilter ()
   from /usr/lib/libkopete.so.1
#32 0xb68d5002 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#33 0xb68d5080 in QObject::event () from /usr/lib/libqt-mt.so.3
#34 0xb69125aa in QWidget::event () from /usr/lib/libqt-mt.so.3
#35 0xb686de56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#36 0xb686ebd6 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#37 0xb70061cd in KApplication::notify () from /usr/lib/libkdecore.so.4
#38 0xb67ff157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#39 0xb6839e0a in QWidget::repaint () from /usr/lib/libqt-mt.so.3
#40 0xb69132e9 in QWidget::repaint () from /usr/lib/libqt-mt.so.3
#41 0xb690d3f2 in QWidget::repaint () from /usr/lib/libqt-mt.so.3
#42 0xb67ee8cc in QETWidget::translateConfigEvent ()
   from /usr/lib/libqt-mt.so.3
#43 0xb67f8e0e in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#44 0xb68124db in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#45 0xb6886947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#46 0xb688686a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#47 0xb686c965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#48 0x0806ddf8 in ?? ()
#49 0xbfa92ee0 in ?? ()
#50 0xbfa93014 in ?? ()
#51 0xbfa9300c in ?? ()
#52 0x00000000 in ?? ()
```



I have tried reinstalling, installing older versions... I have nothing else to try.

Please help!

Matt

---

### Post by pay on 2006-10-14
So it only crashes with the one msn account? Very strange. You could try Gaim or amsn...Even though you would probablt prefer Kopete. Sorry I can't be of more help. Goodluck with the problem.

---

