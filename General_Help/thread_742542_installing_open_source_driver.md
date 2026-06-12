---
title: "installing open source driver"
date: 2008-04-01
forum: General Help
---

### Post by phoenix5002 on 2008-04-01
I was experimenting with different drivers and I want to go back to the Open source ones given to me by Ubuntu.  I found this link explaining how to do that:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I've done this before and it works like a charm.  However there is a small problem now.
If you'll look at the section
**Removing the proprietary fglrx driver**
it says:
> The libGL.so in /usr/lib might also still be the version installed by xorg-driver-fglrx. You can check that very easily, just run:

$ glxinfo |grep vendor

If you see: client glx vendor string: ATI, then the libGL.so is still from ATI.

However, I don't see the ATI string I see SGI.  The article makes no mention of what to do if it does NOT say ATI it just proceeds assuming you did see ATI.  I used to see ATI which is why it worked for me in the past.  I tried continuing anyway but it didn't work.

So what do I do?  Can I get the original libGL.so files that ubuntu gave me?

NOTE: I am using Hardy Heron (8.04), but I don't think it should matter because I had the same open source drivers as I did in Gutsy when I installed Hardy it and they worked just fine.

---

### Post by phoenix5002 on 2008-04-04
can I just download the file online somewhere and just simply replace it?

---

### Post by phoenix5002 on 2008-04-05
well, can someone please tell me what packages the libGL.so file belongs to, and I'll try removing and then reinstalling it.

---

