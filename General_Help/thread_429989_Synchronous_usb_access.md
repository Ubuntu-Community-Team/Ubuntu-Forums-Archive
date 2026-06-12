---
title: "Synchronous usb access"
date: 2007-05-01
forum: General Help
---

### Post by UrbenLegend on 2007-05-01
I don't like how Ubuntu mounts all my usb drives as asychronous access only. I prefer being able to pull out a usb stick without having to click the unmount button on my desktop, like in Windows. How do I enable this in Ubuntu Feisty Fawn?

---

### Post by dcstar on 2007-05-01
> **UrbenLegend said:**
> I don't like how Ubuntu mounts all my usb drives as asychronous access only. I prefer being able to pull out a usb stick without having to click the unmount button on my desktop, like in Windows. How do I enable this in Ubuntu Feisty Fawn?

Removing USB devices with filesystems without "unmounting" is essentially insane - last time I looked Windows has a specific "Stop Device" option that you have to do to avoid potential filesystem corruption.

---

### Post by UrbenLegend on 2007-05-02
Well unmounting before unplug is unnecessary if the writing is synchronous. In Windows, when the progress bar is 100%, it is completely safe to pull it out. However you can't do this in Ubuntu because files are not transferred at once but instead kept in a cache that is written only upon unmount. Yes there is an option in Windows to "unmount" but it is NEVER necessary. Seriously try doing so in Windows or even openSUSE. It works flawlessly without corruption. In Ubuntu however, dealing with usb drives is like dealing with the dark ages. Could someone tell me a solution instead of telling me that I shouldn't do it? Unplugging after a synchronous writing is completely harmless once the file transfer is complete!!!

---

