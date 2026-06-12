---
title: "No right click in Firefox"
date: 2004-10-28
forum: General Help
---

### Post by Circle of Owls on 2004-10-28
My right mouse button appears to be disabled in Firefox, it works fine in other applications, Evolution for instance, and on the desktop, and isn't dependent on the website being viewed. Every website does this, so it isn't a javascript based right-click disabling script. I tried changing the "Disable or replace context menus" option in javascript advanced options anyway, it had no effect. I only have one extension installed, easyGestures, which works fine using the middle button, and doesn't effect the right-click problem, whether it is installed or not. Am I missing something?

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=Circle of Owls]My right mouse button appears to be disabled in Firefox, it works fine in other applications, Evolution for instance, and on the desktop, and isn't dependent on the website being viewed. Every website does this, so it isn't a javascript based right-click disabling script. I tried changing the "Disable or replace context menus" option in javascript advanced options anyway, it had no effect. I only have one extension installed, easyGestures, which works fine using the middle button, and doesn't effect the right-click problem, whether it is installed or not. Am I missing something?[/QUOTE]


Is the page your viewing blocking right clicking?  If so visit [http://mozilla.org](http://mozilla.org) and check the FireFox extensions list.  There is an extension called 'Allow-Right Click'.  Give this a shot.

---

### Post by Circle of Owls on 2004-10-28
No, this happens on every page, on any website. I've tried disabling the javascript blocking anyway, to no effect. The same mouse works fine in Firefox, when dual-booting in Win2k, and also works fine in Firefox in other distros, although I'm not sure why I'd want to use another distro after seeing this one.

---

### Post by FLeiXiuS on 2004-10-29
I believe you have found a bug then.  Post it to bugzilla.ubuntulinux.org

---

### Post by Circle of Owls on 2004-11-04
While researching this issue, I found this bug: [https://bugzilla.ubuntu.com/show_bug.cgi?id=3012](https://bugzilla.ubuntu.com/show_bug.cgi?id=3012). Although the symptoms are not the same, in the 2nd comment Chris Hollenbeck mentions that deleting the .mozilla directory and restarting Firefox restored his context menu. This also worked for me, right-clicking in Firefox works normally now.

---

