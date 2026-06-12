---
title: "Skype in saucy, symbol lookup error in libQtGui.so.4"
date: 2013-11-02
forum: General Help
---

### Post by PBoy on 2013-11-02
Hey guys, having a problem running Skype after having upgraded to 13.10

Skype starts fine, but when I try to log on, I get the following error, and skype closes:

skype: symbol lookup error: /usr/lib/i386-linux-gnu/libQtGui.so.4: undefined symbol: XUnsetICFocus

This file does exist, and I do seem to have the 32 bit libs for Qt installed.

ldd /usr/bin/skype | grep Qt
	libQtDBus.so.4 => /usr/lib/i386-linux-gnu/libQtDBus.so.4 (0xf56ca000)
	libQtWebKit.so.4 => /usr/lib/i386-linux-gnu/libQtWebKit.so.4 (0xf35c0000)
	libQtXml.so.4 => /usr/lib/i386-linux-gnu/libQtXml.so.4 (0xf357f000)
	libQtGui.so.4 => /usr/lib/i386-linux-gnu/libQtGui.so.4 (0xf2acd000)
	libQtNetwork.so.4 => /usr/lib/i386-linux-gnu/libQtNetwork.so.4 (0xf2986000)
	libQtCore.so.4 => /usr/lib/i386-linux-gnu/libQtCore.so.4 (0xf26a1000)
	libQtOpenGL.so.4 => /usr/lib/i386-linux-gnu/libQtOpenGL.so.4 (0xf1bef000)

---

### Post by PBoy on 2013-11-02
For anyone else who has the same issue, this issue resolved itself for me on a reboot. No idea why that would make any difference, I figured ldconfig should pick up any new libraries skype required.

---

### Post by vegan.philosophy on 2013-11-03
Thanks for the solution. I also use Skype and am going to upgrade to 13.10 tomorrow.

---

