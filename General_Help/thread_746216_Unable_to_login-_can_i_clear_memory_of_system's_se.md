---
title: "Unable to login- can i clear memory of system's settings?"
date: 2008-04-05
forum: General Help
---

### Post by eoin09 on 2008-04-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/212308](https://bugs.launchpad.net/ubuntu/+bug/212308) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi

I am using the new 8.04 beta of Ubuntu. Everything was fine until when browsing though menus, on a whim I flipped the display 180 degrees. It did so successfully but then froze up. So I restarted, but turns out its problem because, after entering my password, the screen flips ( i can tell from the mouse cursor) and the desktop does not load, it freezes up again.

My question is- is there a way to make it forget that I set it to do that, and return to what it would do by default when booting?

Thanks

Eoin

---

### Post by jameswillmer on 2008-04-05
yes you want to boot to console only and then change the settings using a text editor

to get to console

1) choose alternative session at login screen
2) OR do ctrl-alt-backspace after logging in - this will kill X and dump you to the command prompt

to edit your flipped settings

1) I don't know but I think you need to edit your /etc/X11/xorg.conf file .... perhaps the 180 flip is in there somewhere....

---

### Post by KeyserSoze93 on 2008-04-06
or press ctrl-alt-f2 to get a virtual console and log in using that...

---

### Post by ghost_ryder35 on 2008-04-06
maybe reconfiguring x will fix it :)
```

sudo dpkg-reconfigure xserver-xorg

```

---

