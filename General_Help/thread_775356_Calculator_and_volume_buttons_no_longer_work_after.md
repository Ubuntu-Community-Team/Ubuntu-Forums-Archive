---
title: "Calculator and volume buttons no longer work after upgrade"
date: 2008-04-30
forum: General Help
---

### Post by Mamono on 2008-04-30
I upgraded to Hardy today and now my calculator, volume and mute buttons no longer work.  They worked flawlessly with Gutsy.  When I hit the calculator button the first time I get a crash notification and then the button no longer does anything.

The other multimedia buttons work with Amarok, such as play/pause, stop, track forward and track backward.  I'm not quite sure what daemon actually launches the calculator so I am unsure on how to restart it to troubleshoot.  If I reboot it will happen again the first time, but then no more.

I have a Dell Dimension 9100 and I'm using a Logitech Cordless Comfort Keyboard/Mouse combo.

Does anyone have any ideas?

---

### Post by Mamono on 2008-04-30
Ok, here's an update.  The volume and mute buttons work fine.  They stop working after I hit the calculator button which causes kded to crash.  Relaunching kded does not allow me to recreate the problem.

Here is the output from the crash daemon:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread 0xb682a6c0 (LWP 7217)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0x692f6572 in ?? ()
#7  0xb785266f in KConfigBase::readEntry () from /usr/lib/libkdecore.so.4
#8  0xb78b6692 in KConfigBase::readEntry () from /usr/lib/libkdecore.so.4
#9  0xb635c326 in KMilo::GenericMonitor::launch ()
   from /usr/lib/kde3/kmilo_generic.so
#10 0xb635c5f7 in KMilo::GenericMonitor::launchCalculator ()
   from /usr/lib/kde3/kmilo_generic.so
#11 0xb635f71e in KMilo::GenericMonitor::qt_invoke ()
   from /usr/lib/kde3/kmilo_generic.so
#12 0xb78331d3 in KGlobalAccelPrivate::activate ()
   from /usr/lib/libkdecore.so.4
#13 0xb78bf92e in KGlobalAccelPrivate::x11KeyPress ()
   from /usr/lib/libkdecore.so.4
#14 0xb78bfb4c in KGlobalAccelPrivate::x11Event ()
   from /usr/lib/libkdecore.so.4
#15 0xb78ceaea in KApplication::x11EventFilter ()
   from /usr/lib/libkdecore.so.4
#16 0xb71474a0 in ?? () from /usr/lib/libqt-mt.so.3
#17 0xbf97c0d4 in ?? ()
#18 0xbf97be98 in ?? ()
#19 0x00000001 in ?? ()
#20 0x00709650 in ?? ()
#21 0x00000086 in ?? ()
#22 0xb7709650 in ?? () from /usr/lib/libqt-mt.so.3
#23 0xbf97bd38 in ?? ()
#24 0xb7157aaf in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
Backtrace stopped: frame did not save the PC

---

### Post by Mamono on 2008-04-30
Well, I found a solution to my problem but I'm not 100% sure the underlying problem is fixed.  Basically, I associated SpeedCrunch with the calculator button through the system settings.  The calculator now pops up when I hit the button and everything else works normally.

When I went to make the change, though, the association said none so I'm thinking there was something else in KDE that was handling that function.

---

### Post by sir_cheats_a_lot on 2008-10-12
in any case the binding of the calculator key to the calculator app is a good enough work around.

 According to:
#10 0xb635c5f7 in KMilo::GenericMonitor::launchCalculator ()

 This appears to be an issue caused with Kmilo. i'll know shortly as my system isn't completely up to date, and there is an update for it so im grabbing that real quick. will post back here after installing and rebooting.
  oh good.. its done installing. *reboots*

---

### Post by sir_cheats_a_lot on 2008-10-12
still does it with the updated version, and with kmilo-legacy.. but i did find this:

[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/204534](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/204534)

i guess kmilo is being removed from intrepid. no idea what they are going to use in its place though.   so in the mean time just keep speed crunch on the shortcut key.

going to try the kde4 version of it to see if it works...i won't be holding my breath though.

---

