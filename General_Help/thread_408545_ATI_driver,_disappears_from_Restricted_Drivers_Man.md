---
title: "ATI driver, disappears from Restricted Drivers Manager"
date: 2007-04-13
forum: General Help
---

### Post by Toadmund on 2007-04-13
OK, I looked in RDM, and LO, there was my ATI driver, enabled but not being used. I was happy to see this because it was gone missing for awhile.
So I follow these instructions to get 'er going:
[http://ubuntuforums.org/showthread.php?t=399643&highlight=feisty+ati]("http://ubuntuforums.org/showthread.php?t=399643&highlight=feisty+ati")
So after I do this:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Then after that, the author of the thread insructs to check RDM to enable the driver, well my driver already is, but  I check it anyway, and it's gone again! Not there!
Why is it that when I do the update, upgrade, dist-upgrade it taketh away my ATI driver from RDM?

Why do I have this problem?

How do I get my driver back into Restricted Driver Manager?:confused:

---

### Post by Toadmund on 2007-04-17
OK, it's back again in Restricted Driver management, it says it's enabled *and* in use this time.
However I put 'fglrxinfo' in terminal and stil this:
```
toad@toad-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```
:confused:

---

### Post by reality_hunter on 2007-04-24
huhm, it seems like the extension "XFree86-DRI" is missing on display (0.0)
but, at the moment I am not too sure how to get that.

---

### Post by zasf on 2007-05-24
imho you should file a bug in launchpad

Matteo

---

