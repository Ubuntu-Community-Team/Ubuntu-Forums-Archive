---
title: "SSH or &quot;Connect to Server&quot; broken in Feisty (GUI/Nautilus)"
date: 2007-04-23
forum: General Help
---

### Post by altonbr on 2007-04-23
Whenever I go to Places > Connect to Server.. on my GUI client, and I add in all the correct information and select "connect", nothing happens.

I've tried "killall nautilus", but to no avail. I rebooted the computer, and all of a sudden my 6 failed attempts to connect, have mounts on my desktop.

So after unmounting all but the first attempt, I double click the icon, and nothing happens. I right-click it and select "Browse Folder". That worked... but only once. Now nothing even pops up when I double-click or right-click and select "Open" or "Browse Folder".

Has anyone else experienced this? What about using video recording software so I can record this 'dance' I have to do?


PS: A similar problem happened to me in Edgy, so I wiped my drive and went back down to Dapper for stability. I went back up to Feisty by upgrading to Edgy and then to Feisty. Is it possible that Edgy broke one of my config files, or is this a known bug?

---

### Post by rich.bradshaw on 2007-04-23
I thought this but its normal.

Once you have clicked connect, go to places on the menu and the server you added is there. Just put in your password and it will connect.

It should really come up with a box telling you that it has added it to the places menu.

---

### Post by altonbr on 2007-04-23
No, when I create a new server link, it doesn't show up anywhere. Then when I do restart, and I can't load it by double-clicking.

It seems as though that Places > "Server Name" trick worked for connecting, but what about the disappearing new link?

---

### Post by nathanembery on 2007-04-23
I just wanted to second this. Connect to Server doesn't do anything on a fresh install until after you reboot. Then, upon logging back in, all the previous attempts are there on the desktop. After the reboot everything appears to work correctly.

---

### Post by bradlis7 on 2007-11-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/nautilus/+bug/29391](https://bugs.launchpad.net/nautilus/+bug/29391)
----------------------------

"Connect to Server" doesn't work for me with ssh or ftp login. They do come up on restart, but that's not acceptable. It's probably a nautilus bug, but I don't really know.

---

### Post by altonbr on 2007-11-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/120220](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/120220) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I also submitted this bug on 2007-06-13. Currently it's considered "wishlist" priority.

---

