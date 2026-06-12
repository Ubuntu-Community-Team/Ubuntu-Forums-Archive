---
title: "[kde] how do I turn off the sound effects in kmymoney?"
date: 2013-09-16
forum: General Help
---

### Post by boumbh on 2013-09-16
This is an answer for the question that was asked in [this thread]("http://ubuntuforums.org/showthread.php?t=1848651"):

[QUOTE="josephellengar the September 23rd, 2011"]I installed kmymoney in gnome, so I can't use the KDE control  center to turn off the sound effects. I don't even have KDE installed.  Is there any way to turn off the sounds effects?

Thanks![/QUOTE]
The sound effects in KDE applications must be turned off at KDE system administation level.

**_First way:_** You can install the KDE administration interface, it's about 1kB:
```
sudo apt-get install systemsettings
```

Then run it:
```
systemsettings
```

Click on **Application and System Notifications**, **Player Settings**, select the **No audio Output** radio, and then the **Apply** button.

**_Second way:_** If you don't wish to install a stupid administration interface just to get rid of such anoyance, you can also try this:

Edit the **~/.kde/share/config/knotifyrc** file and add:

```
[Sounds]
No sound=true
Use external player=false
Volume=100
```

Just for the record, here is my **~/.kde/share/config/knotifyrc**:

```
[Misc]
LastConfiguredApp=Accessibility

[Phonon::AudioOutput]
KNotify_Volume=1

[Sounds]
No sound=true
Use external player=false
Volume=100
```

If you are a paranoid like me, you may also want to copy this file into **/usr/share/kde4/config**.

---

