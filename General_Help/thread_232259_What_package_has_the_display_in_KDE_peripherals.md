---
title: "What package has the display in KDE peripherals?"
date: 2006-08-08
forum: General Help
---

### Post by aysiu on 2006-08-08
So, I found out that I like *kde-core* a lot more than I like *kubuntu-desktop*.

For some reason, it's faster (Firefox takes three seconds to load instead of twelve seconds), and it has also only what I decide to put into it (no Speedcrunch or Akregator).

The only thing I'm missing (that I *did* have with *kubuntu-desktop*) is **Display** under the Peripherals section of *kcontrol* or *systemsettings*.

I've got Mouse, Keyboard... even Joystick (I don't have a joystick!), but no Display.

Anyone know what package I have to install to get Display to appear in the Control Center? I could install *kubuntu-desktop*, but that seems overkill... and would damage the good thing I've got going with *kde-core*.

I've Googled around but found nothing on this.

---

### Post by msak007 on 2006-08-08
I believe the pacakge you're looking for is "kde-guidance"? Not sure if you have it installed as I have kubuntu-desktop not kde-core, but kde-guidance is the package that includes the displayconfig app that's used for the System Settings / kcontrol module.

---

### Post by aysiu on 2006-08-08
Thanks, msak007! I'll give that a shot. It looks as if it'll do the trick.

---

### Post by msak007 on 2006-08-08
No problem, let me know if that resolves it for you.

---

### Post by aysiu on 2006-08-08
That is the package, but when I click on **Display**, the Control Center crashes, and I get this: ```
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
[Thread debugging using libthread_db enabled]
[New Thread -1231882560 (LWP 5762)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0xb72f4f83 in QWidget::paletteBackgroundColor ()
   from /usr/lib/libqt-mt.so.3
#7  0xb6244fb3 in DominoStyle::polish ()
   from /usr/lib/kde3/plugins/styles/domino.so
#8  0xb7255754 in QApplication::polish () from /usr/lib/libqt-mt.so.3
#9  0xb72f61d5 in QWidget::polish () from /usr/lib/libqt-mt.so.3
#10 0xb59e603c in sipQVButtonGroup::polish ()
   from /usr/lib/python2.4/site-packages/qt.so
#11 0xb724f474 in QLayout::totalMinimumSize () from /usr/lib/libqt-mt.so.3
#12 0xb7250726 in QLayout::activate () from /usr/lib/libqt-mt.so.3
#13 0xb7250ada in QLayout::eventFilter () from /usr/lib/libqt-mt.so.3
#14 0xb72be002 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#15 0xb72be080 in QObject::event () from /usr/lib/libqt-mt.so.3
#16 0xb72fb5aa in QWidget::event () from /usr/lib/libqt-mt.so.3
#17 0xb738572e in QGroupBox::event () from /usr/lib/libqt-mt.so.3
#18 0xb7359fec in QButtonGroup::event () from /usr/lib/libqt-mt.so.3
#19 0xb59e753e in sipQVButtonGroup::event ()
   from /usr/lib/python2.4/site-packages/qt.so
#20 0xb7256e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb7257bd6 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb7923d7d in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb71e8157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#24 0xb72584a7 in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#25 0xb72585ae in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#26 0xb71fb548 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#27 0xb726f947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#28 0xb726f86a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#29 0xb7255965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#30 0xb680aabd in kdemain () from /usr/lib/libkdeinit_kcontrol.so
#31 0xb7f6c4f4 in kdeinitmain () from /usr/lib/kde3/kcontrol.so
#32 0x0804e063 in ?? ()
#33 0x00000001 in ?? ()
#34 0x0813fa20 in ?? ()
#35 0x00000001 in ?? ()
#36 0x00000000 in ?? ()
```

---

### Post by msak007 on 2006-08-09
I know I've had some problems in the past with the module not loading if there were some entries in xorg.conf that it didn't like, but it never outright crashed the control center - it simply said that some files were missing or couldn't be loaded in the window. It looks from the screenshot like you're using an OSX-like theme. I know some themes have problems with the KDE-GTK engine. Try possibly changing your theme / style to a KDE standard one such as Crystal, Keramik, or Plastik and then try again.

---

### Post by aysiu on 2006-08-09
You're right! It didn't crash on Plastik.

I was using a Domino style with a Baghira window decoration. Thanks for that. I'll try to figure out how to get it to work with those themes.

Thanks again, msak007. You've been a great help!

---

### Post by msak007 on 2006-08-09
No problem at all! I'm glad to be helping you once for a change :). I thought you might be using Domino because I did see that in the output. In fact, it was almost identical to the output someone posted [here]("http://www.kde-look.org/content/show.php?content=42825") on the KDE-Look.org entry for that theme when KMyMoney crashed on them using that theme but not another one. I'm not sure there's a way around it, you may have to submit a bug report with the theme designer.

---

