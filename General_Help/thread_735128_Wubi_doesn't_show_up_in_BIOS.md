---
title: "Wubi doesn't show up in BIOS"
date: 2008-03-25
forum: General Help
---

### Post by X-Legs on 2008-03-25
I am working on a Windows XP pro on a limited account. I used Wubi 7.4 to install Ubuntu 7.10. The install goes without a hiccup, but when I reboot I have no choice between Windows and Ubuntu. What do I do now?

---

### Post by Tomatz on 2008-03-25
I would say you need to install it as admin :)

---

### Post by X-Legs on 2008-03-25
Is there any workaround or way to make it boot? Is there is string I can add to a LiveCD boot or something?

---

### Post by ago on 2008-03-25
If you have XP you should see a "Ubuntu" entry in C:\boot.ini
Note that boot.ini is a hidden file and you might have to set the option to show hidden files in windows explorer.

---

### Post by X-Legs on 2008-03-25
I can see it, but it says "Access denied." Probably the problem. Now, can I boot off my LiveCD and point to the Linux bootloader or something? Is there an alternate way to boot into this Ubuntu?

---

### Post by ago on 2008-03-25
> **X-Legs said:**
> I can see it, but it says "Access denied." Probably the problem.
Yes, if you cannot edit boot.ini, neither can wubi...

> Now, can I boot off my LiveCD and point to the Linux bootloader or something? Is there an alternate way to boot into this Ubuntu?
You can boot off the LiveCD and install from there, which is always the preferred way to do a long term installation, be aware that it will require a dedicated partition and replace the windows bootloader (with a better one).

---

