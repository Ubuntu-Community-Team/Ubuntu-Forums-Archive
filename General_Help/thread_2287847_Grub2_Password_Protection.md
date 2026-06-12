---
title: "Grub2 Password Protection"
date: 2015-07-22
forum: General Help
---

### Post by ronjeanjr on 2015-07-22
Sorry to start a new thread, but the original thread was [prematurely] closed.  I have Ubuntu Mate 14.04.2 LTS & used Grub Customizer as a starter kit [since I'm new to Grub2].  The original thread @ [http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019) failed to address a problem with formatting preventing the safe addition of passwords to menu entries....or even anywhere!  If you cross reference the answers from that thread and the entire file dumps I'm about to put below, you will all see that there needs to be answered: **"How do I password protect menu entries of Grub2 or even just the command line of Grub2 when I have 10_linux_proxy and other files instead of just the originals?"**

[COLOR=#ff0000]**10_linux_proxy**[/COLOR]

#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/linux' | /etc/grub.d/bin/grubcfg_proxy "+*
+#text
-'Ubuntu'~851f3966407f83c2f3bee5912a2228aa~
-'SUBMENU' as 'Advanced options for Ubuntu'{-'Advanced options for  Ubuntu'/*, -'Advanced options for Ubuntu'/'Ubuntu, with Linux  3.16.0-43-generic'~85b62a8c86a22e5bdfe6f17aa9269e3d~, -'Advanced options  for Ubuntu'/'Ubuntu, with Linux 3.16.0-43-generic (recovery  mode)'~b9f9e68db1c19294c410148483d2207d~, -'Advanced options for  Ubuntu'/'Ubuntu, with Linux  3.16.0-33-generic'~83600a9f0ea75ef1babfa9866f39c317~, -'Advanced options  for Ubuntu'/'Ubuntu, with Linux 3.16.0-33-generic (recovery  mode)'~3481dc7218e41b032549e41c2c31b622~}
"

[COLOR=#ff0000]**30_os-prober_proxy**[/COLOR]

#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/os-prober' | /etc/grub.d/bin/grubcfg_proxy "+*
+#text
+'Windows 7 (loader) (on /dev/sda1)'~cb7aecf86ea33f58de9e54af05184ec5~ as 'Windows 7'
"

[COLOR=#ff0000]**31_linux_proxy**[/COLOR]

#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
sh -c 'echo "### BEGIN /etc/grub.d/proxifiedScripts/linux ###";
"/etc/grub.d/proxifiedScripts/linux";
echo "### END /etc/grub.d/proxifiedScripts/linux ###";
echo "### BEGIN /etc/grub.d/proxifiedScripts/memtest86+ ###";
"/etc/grub.d/proxifiedScripts/memtest86+";
echo  "### END /etc/grub.d/proxifiedScripts/memtest86+ ###";' |  /etc/grub.d/bin/grubcfg_proxy  "+'Ubuntu'~851f3966407f83c2f3bee5912a2228aa~ as 'Linux'
-*
-#text
+'SUBMENU'  as 'Advanced options for Ubuntu'{+'Advanced options for Ubuntu'/*,  +'Advanced options for Ubuntu'/'Ubuntu, with Linux  3.16.0-43-generic'~85b62a8c86a22e5bdfe6f17aa9269e3d~, +'Advanced options  for Ubuntu'/'Ubuntu, with Linux 3.16.0-43-generic (recovery  mode)'~b9f9e68db1c19294c410148483d2207d~, +'Advanced options for  Ubuntu'/'Ubuntu, with Linux  3.16.0-33-generic'~83600a9f0ea75ef1babfa9866f39c317~, +'Advanced options  for Ubuntu'/'Ubuntu, with Linux 3.16.0-33-generic (recovery  mode)'~3481dc7218e41b032549e41c2c31b622~, +* from  '/etc/grub.d/proxifiedScripts/memtest86+', +'Memory test  (memtest86+)'~72686e6c3d31ab0ff44273e7dad60947~ from  '/etc/grub.d/proxifiedScripts/memtest86+', +'Memory test (memtest86+,  serial console 115200)'~588114722beced3d8e0c3ad242996d2c~ from  '/etc/grub.d/proxifiedScripts/memtest86+'}
" multi

---

### Post by howefield on 2015-07-22
Thread moved to the "*General Help*" forum.

---

