---
title: "ATI (fglrx) screen resoltuion ?  fglrx uses it's own resolution modes?"
date: 2007-06-09
forum: General Help
---

### Post by tajmox on 2007-06-09
I'm trying to get a custom resolution using fglrx.
xorg.conf doesn't even have my current resolutions in it, so of course editing that didn't change anything.
I also tried aticonfig --resolution=1680x1050,1280x800,1280x768,1280z720
And got this error:
Error: Section # expected
aticonfig: parsing the command-line failed.

I even did dpkg-reconfigure xserver-xorg to add the resolutions, but after making fglrx my driver, it seems fglrx uses it's own resolution mode lines somewhere, despite what xorg.conf says.   
So where can I change the resolution?

Thanks!

---

