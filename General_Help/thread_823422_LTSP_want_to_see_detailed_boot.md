---
title: "LTSP want to see detailed boot"
date: 2008-06-09
forum: General Help
---

### Post by clarkey on 2008-06-09
I am trying to debug a problem with my LTSP thinclient it seems to get stuck for a while trying to load something to do with ac97 when its loading hardware now the reason im so vague is I have only seen it once or twice because I cant seem to convince the thin client not to show the splash screen. Everything online tells me to go to /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default    and remove quiet splash from there Ive done that but the splash screen is still there, Ive also removed quiet splash from /opt/ltsp/i386/boot/pxelinux.cfg/default   also with no success any ides?

---

### Post by darkazurka on 2008-06-22
Is your solution found in /boot/grub/menu.lst , or is it a special case for this LTSP?

Now if my reply is no use: Try opening Synaptic->Check the packages you've installed (mine are called ltsp-client , ltsp-client-core etc etc. If you click on a package **you've installed** go to the *Installed Files* tab and see where your files have been installed. After some quite extensive(and time consuming research) it's very possible you'll understand where to look.

Actually personally I recommend to search or **look out for** the /etc/ directory. There are stored all configuration files. (while watching the *Installed Files* tab (for every related package) in Synaptic).

---

