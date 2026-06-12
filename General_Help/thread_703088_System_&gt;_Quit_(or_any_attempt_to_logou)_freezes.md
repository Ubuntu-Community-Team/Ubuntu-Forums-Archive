---
title: "System &gt; Quit (or any attempt to logou) freezes system."
date: 2008-02-21
forum: General Help
---

### Post by JeanNiBee on 2008-02-21
I'm not sure why but any attempt by me to log | lock my desktop etc freezes my system.

I had the special effects enabled through my Nvidia Graphics Card (using restricted drivers) and thought maybe this was causing the issue but turning it all odd didn't help.

Any help would be great, thanks.

---

### Post by DJ_Peng on 2008-04-29
I'm also having this issue in Hardy but I found something that may work. A suggestion on [Bug #150846 Quit button freezes screen but does not present Log out etc. options dialog]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/150846/comments/10") suggests going to System > Preferences > Sessions and make sure Power Manager is set to run at startup. I'm about to reboot now to see if that helps, but I wanted to pass it along to you while I do in case it works for you but not for me. You may also want to manually run gnome-power-manager so it's running when you try to reboot.

*ETA: I made sure gnome-power-manager was running and I get the Quit dialog again with no problem. There seems to be something about that app not running that hangs the system when you try to quit.*

---

