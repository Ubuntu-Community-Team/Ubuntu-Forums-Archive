---
title: "Can I run gnome desktop through SSH?"
date: 2008-02-25
forum: General Help
---

### Post by MarcG on 2008-02-25
I'm setting up a MythTV box on a standard 640X480 TV and am having a hard time going through all the configurations on that screen size. Some of MythTV's menus are way too small to resolve on the screen. So what I would like to do is run all the configuration from my other Ubuntu PC through SSH.

The MythTV config stuff is fine, but I would also like to use the different desktop applications on the non-MythTV box. Is there any way to get the complete desktop to run in an SSH X-window?

Thanks.

--Marc

---

### Post by The Cog on 2008-02-25
Yes you can. Use ssh with the -X switch and that will tunnel X back to your desktop.

But I don't recommend running gnome-desktop because it will put its own top and bottom gnome panels on top of yours which is very confusing. But you can run any other X application (assuming you know the program name to launch it).

---

### Post by bodhi.zazen on 2008-02-25
Yes you can run gnome desktop over X

use ssh -X

Best to start a new X session (on say Ctrl-alt-F8 ) leaving your local desktop on Ctrl-Alt-F7 (Yes, you can have multiple X sessions).

[https://help.ubuntu.com/community/SSHHowto#head-3dfe4cbc16557b30eeb4d860b919ef926c9e67f1](https://help.ubuntu.com/community/SSHHowto#head-3dfe4cbc16557b30eeb4d860b919ef926c9e67f1)

Or start X in Xephyr : [http://ubuntuforums.org/showthread.php?p=3816948](http://ubuntuforums.org/showthread.php?p=3816948)

You can also forward vnc over ssh.

---

### Post by MarcG on 2008-02-25
Thanks! That's what I was looking for.

--Marc

---

