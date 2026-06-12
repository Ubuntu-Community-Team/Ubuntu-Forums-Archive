---
title: "[SOLVED] Large file disappears without a trace"
date: 2007-12-30
forum: General Help
---

### Post by Aurora on 2007-12-30
Hello,

I've been using Ubuntu since Warty, and this has never happened before.

I downloaded an .iso for a distro to my desktop.  When the download ended, there was no icon of the file on the desktop; I could not find it with the file browser, either.  When I tried to download the file again, Firefox informed me that the file already existed on the Desktop. I tried putting the file name in the search window of the browser (I use Thunar) and I got the error message:

"The folder contents could not be displayed.

The name org.freedesktop.Tracker was not provided by any .service files"

So, where would over half a gig of data be hiding?

Thanks,

Paul in Seattle

---

### Post by aysiu on 2007-12-30
Can you try looking for it in the terminal? ```
cd ~/Desktop
ls -a
```

---

### Post by nick_h on 2007-12-30
or try:
```
find ~ -name "*.iso"
```

---

### Post by Aurora on 2007-12-30
Neither of those commands turned up anything, and I figured out why.  I wanted to download the file into an external drive with root-only access, so I opened up in the terminal with sudo firefox.  I could not get Firefox to put the file where I wanted; instead it ended up on the Desktop of *the Root account*.  When I searched the Desktop of my normal user account, of course it was not there, but Firefox kept saying it was on the Desktop...it did not say which user account.

One of those should-be-obvious things that are so easy to miss...in the meantime the above commands helped me clean out several gigabytes of old .iso's, so it was well worth learning those tools.  So my thanks to you,

Paul

---

### Post by aysiu on 2007-12-30
Well, first of all, if you decide to launch Firefox as root, the command should be ```
gksudo firefox
``` and not *sudo firefox*

It's best to launch Firefox as user and then, once you've downloaded the file, copy the file as root. Operating web-based applications as root is not a good idea security-wise.

---

