---
title: "[SOLVED] Won't boot Windows."
date: 2008-06-04
forum: General Help
---

### Post by abenitoc on 2008-06-04
Hi, I have a Windows SP2 an Ubuntu Hardy installed in the same machine. I've been working fine with both until I accidentally erased some files in the windows partition that were needed by the grub to boot. When I tried to boot windows, it said that the "ntldr" was needed. So I booted ubuntu and restored the files to it's place. Then I was again able to boot Windows. But the next morning I tried to do the same and when I selected Windows from the menu the computer just turned-off and restarted again at the menu, so no I'm stuck there, only booting from the Ubuntu partition.

Does anyone knows which files the Windows partition needs and which I may had deleted? Can I reconfigure the grub or something? Do I have to format and reinstall Ubuntu so it recognizes again windows?

I'd appreciate the help, I'm a beginner in linux... Thanks!

---

### Post by Prospero2006 on 2008-06-04
Reinstalling Ubuntu to make it recognize Windows is not the way to do it.

You have to work with grub directly.

The configuration file is in /boot/grub/menu.lst

You can also pass grub commands manually by pressing e at the selection menu.

What I would do:

I'd insert your windows recovery disk and see if you can't hit 'r' in there for a self repair.

--Be careful though. Don't let it eat your Ubuntu.

---

### Post by babylon2233 on 2008-06-04
You need to recover your ntldr.

---

### Post by abenitoc on 2008-06-07
> **babylon2233 said:**
> You need to recover your ntldr.

How can I do that? The file I think was not edited, I only moved it to the trash and back.

---

### Post by abenitoc on 2008-06-23
I did use the Windows CD to recover the damaged files, thank you all!

---

