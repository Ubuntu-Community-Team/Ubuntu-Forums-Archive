---
title: "No Way to Navigate (Unity)"
date: 2012-10-22
forum: General Help
---

### Post by Katla on 2012-10-22
I just ran updates from the manager. After getting a lot of error messages while in that process, everything took and now my system boots as quick and as clean as it ever has. So that's nice.

What's not nice is that once everything boots, I've got no way to navigate anywhere as my Unity menus are gone. The top taskbar as well as the sidebar. I'm not too fluent in Linux, so I can't use the terminal to open much. I got to Firefox using my Skype application, which pops up when I log on.

I hear that 12.10 no longer supports Unity 2D, which I suspect may be the problem. I assume when I used the update manager it upgraded me. So how do I switch to 3D, and/or get my taskbars back?

I appreciate the help.

---

### Post by Paqman on 2012-10-22
Yes, Unity 2D is no longer supported, so if that's what you're using you'll need to log out and click the little icon next to your user name and switch to a desktop environment that you do have.

---

### Post by Katla on 2012-10-22
But how do I log out without any of the taskbars? When I do a reboot I go straight into Unity without needing to log in, and miss the chance to choose.

---

### Post by ajgreeny on 2012-10-22
Failing any other way, use **Alt Gr+Print Screen+K** which will kill the xsession and should get you back to the login screen.

There may be "softer" ways, but if nothing is running or needs saving, this way should be fine.

---

### Post by Katla on 2012-10-22
> **ajgreeny said:**
> Failing any other way, use **Alt Gr+Print Screen+K** which will kill the xsession and should get you back to the login screen.

There may be "softer" ways, but if nothing is running or needs saving, this way should be fine.

That worked. However, looking at the log-in screen, it's telling me I've still got 12.04. I tried using just "Ubuntu", but logging in with that didn't fix my taskbar issue. So I did it again and chose "Ubuntu 2D", and that did it. I'm glad to have functionality again, at any rate. 

Thank you.

---

