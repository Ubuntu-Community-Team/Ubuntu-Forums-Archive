---
title: "Ubuntu run in VMware, Graphics Card Doesn't Work?"
date: 2007-03-21
forum: General Help
---

### Post by tsav87 on 2007-03-21
I have dual booted my computer with Ubuntu Edgy and Windows XP ME, but I didn't like havening to switch back and forth betweens OSs just to play games on one, and surf the web on the other.

I went ahead and reinstalled Windows as the only OS on my HD.  Then I downloaded VMware for windows and the Ubuntu Dapper for VMware.

I am having a problem getting it to install the nVidea graphics card.  The usual route doesn't work.  After I reboot Ubuntu it won't load.  What's the deal?

If I could get the graphics card to work, the method of using VMware with Windows to run Ubuntu is so much better than partitioning off the HD and dual booting.

---

### Post by hikaricore on 2007-03-21
VMWare doesn't actually support the use of your video card, if this is what I think you're asking.

It only uses it's virtual video hardware.

Which is why vmware can not do direct rendering and other great video tricks.

---

### Post by tsav87 on 2007-03-21
Is there any other way to run a virtual OS that supports the card?

---

### Post by hikaricore on 2007-03-21
I don't believe so, but there are versions of vmware that can do virtual direct rendering,
I believe this is alpha/beta stages if that, and only in the paid versions of vmware.   And I
still am pretty sure this won't use your video card except indirectly.

(anyone feel free to correct me if I'm wrong)

---

