---
title: "eclipse and ubuntu 14.04"
date: 2014-04-30
forum: General Help
---

### Post by meitnerium on 2014-04-30
Hello,
       I tried eclipse on ubuntu 14.04. The ubuntu package of eclipse is version version on repository is 3.8. I want to use photran, and the last version of photran is available only on kepler  version (4.3). So I downloaded the last version of eclipse (4.3.2). When I run it, I often have crash, with error like this one :

[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:000] Using Gtk2 toolkit
[000:001] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:001] No bp log location saved, using default.
[000:001] Browser XEmbed support present: 1
[000:001] Browser toolkit is Gtk2.
[000:001] Using Gtk2 toolkit
No bp log location saved, using default.
[000:000] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:001] No bp log location saved, using default.
java version "1.7.0_51"
OpenJDK Runtime Environment (IcedTea 2.4.6) (7u51-2.4.6-1ubuntu4)
OpenJDK 64-Bit Server VM (build 24.51-b03, mixed mode)

Do you have any clues?

---

### Post by Germe82 on 2014-05-07
Try to add *-Dorg.eclipse.swt.browser.DefaultType=mozilla* to your eclipse.ini 

Source: [http://comments.gmane.org/gmane.comp.java.openjdk.distro-packaging.devel/27399](http://comments.gmane.org/gmane.comp.java.openjdk.distro-packaging.devel/27399)

---

