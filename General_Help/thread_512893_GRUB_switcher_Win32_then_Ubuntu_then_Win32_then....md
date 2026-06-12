---
title: "GRUB switcher: Win32 then Ubuntu then Win32 then..."
date: 2007-07-29
forum: General Help
---

### Post by Salmonman on 2007-07-29
I was wondering if there was a setting or configuration file I could edit so that GRUB switches the default boot OS every time it restarts ala:

boot 1: Win32
boot 2: Ubuntu
boot3: Win32
boot 4: Ubuntu
e.t.c

It would be great to have this setup or even better a way of picking which should be default the next time it boots so that I can run it remotely as a headless server.

---

### Post by mannheim on 2007-07-30
Rather than alternate, you have the default be for grub to boot to Linux, and set it up so that you can choose at any time to boot **once** to Windows. (After that, it will return to Linux.) Instructions and a clearer explanation of what I am trying to say are in the[ grub documentation.]("http://www.gnu.org/software/grub/manual/html_node/Booting-once_002donly.html")

---

### Post by mannheim on 2007-07-30
And if you really want to alternate, I guess you could do (assuming linux is on hda1 and Windows is on hda2):

```
     default saved
     timeout 10

     title Ubuntu
     root (hd0,0)
     kernel /boot/vmlinuz-whatever
     savedefault 1

     title Windows
     root (hd0,1)
     savedefault 0
     makeactive
    chainloader +1

```

Disclaimer: I've never tried this.

---

