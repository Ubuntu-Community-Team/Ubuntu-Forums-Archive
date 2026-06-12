---
title: "Synclient settings explained?"
date: 2015-10-11
forum: General Help
---

### Post by vasa1 on 2015-10-11
Can someone please point me to a link that explains the output seen on running *synclient* in a terminal?

I have a Dell Inspiron 1545 laptop with ```
AlpsPS/2 ALPS GlidePoint id=14	[slave  pointer  (2)]
```as the touchpad but most articles on touchpads deal with Synaptics touchpads.

Edit: I found one source (even though it's for Synaptics): [http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html)

---

### Post by ajgreeny on 2015-10-11
Are those defaults ones you have set or are they the system defaults after installing the system?

Just for info, there is also **man synaptics** of course, and also the community help at [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) though I agree that neither of those help with actual default settings.

---

### Post by vasa1 on 2015-10-11
> **ajgreeny said:**
> Are those defaults ones you have set or are they the system defaults after installing the system?

Just for info, there is also **man synaptics** of course, and also the community help at [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) though I agree that neither of those help with actual default settings.
Thanks for responding.

The file is what I see on running the *synclient* command without making any changes and after a reboot. So I'm guessing they're system defaults. I'm exploring what I can change but from what I've read, those changes do not survive a reboot. If I want to make a persistent change, I'll need to stick it in my autostart.

I'm looking at *man synaptics*. That's quite informative.

---

### Post by ajgreeny on 2015-10-11
In the past I made the synclient settings work in all sessions by using a simple bash script added to startup applications which ran after session startup, though I had to use a sleep option of a few seconds to allow the desktop to start fully before the script was executed properly.

Now I use a desktop machine I have no need for the script any more, and I can't remember what its content was but it was very simple both to write and employ.

---

