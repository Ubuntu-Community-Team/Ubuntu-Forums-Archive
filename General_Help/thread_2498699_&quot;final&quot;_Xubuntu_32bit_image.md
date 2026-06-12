---
title: "&quot;final&quot; Xubuntu 32bit image?"
date: 2024-06-24
forum: General Help
---

### Post by v47 on 2024-06-24
so I've [managed to get the last 32bit build going]("https://ubuntuforums.org/showthread.php?t=2498502"), but to be able to do that again in the nearby future (disk fail, whatever), right now I still need to be able to download updates from the ubuntu servers. and I'm very sure at some point, someone will flip a switch and they will be no more - would it be possible to create an iso image of Xubuntu 18.04.6 with all the available OS updates that exist already applied, and maybe a few applications (sysinfo, Chromium) loaded out of the box? because afaik applications are also dependent on online sources, once they go down, you are out of luck (even the [standalone deb package of Chromium]("https://launchpad.net/ubuntu/bionic/i386/chromium-browser") downloads additional stuff from somewhere during install as far as I can tell).

basically, I would like to go fully offline with this install. thanks.

---

### Post by currentshaft on 2024-06-24
Whenever you're trying to do something and find it's difficult, if not impossible, stop and ask yourself: what problem am I trying to solve?

Why do you want to run an operating system that's been deprecated for three years?

---

### Post by v47 on 2024-06-24
because it's fun?

---

### Post by currentshaft on 2024-06-24
Sure, then I would use dd to make a copy of the volume and copy it on additional storage devices when I want to clone it. But I wouldn't advise connecting something that old to the Internet.

---

### Post by oldfred on 2024-06-24
Are you sure it is a 32 bit system. Windows was installed in 32 bit mode to many 64 bit systems.
And some lightweight systems had 32 bit UEFI boot, but were 64 bit systems.

And almost all 32 bit systems are prior to 2012 when Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives.
Only a few table type systems may be 32 bit.

A Raspberry Pi will offer faster system and can be fun.

---

### Post by v47 on 2024-06-24
yeah, cloning is my backup plan. so, no way of pulling those updates into some offline form to which I could point the install when the servers go down?

yeah, it's 32bit, one of the last 32bit atom cpus.

---

### Post by him610 on 2024-06-24
@v47

> The most recent version of Debian is Debian 12.5, codenamed "Bookworm", which was released on February 10, 2024.
*> Debian users will still be able to install a 32-bit userland, run 32-bit Debian inside various types of container, and build applications for x86-32… but you can expect that the x86 version of Debian 13 "Trixie", which is planned for 2025, will only support 64-bit hardware.*
Maybe you should get 32-bit Debian while it is still available and supported.
It can probably be installed with XFCE as DE.

---

### Post by ajgreeny on 2024-06-25
I would agree that Debian-Xfce 32bit system installed with out setting a root password and ensuring that non-free repos are enabled will probably be your best option.

I have it, though hardly ever used, on a netbook with probably the same 32bit Atom CPU and only 1G ram; it just about runs but is more or less useless with any modern applications such as chromium or Firefox browsers, Libreoffice, etc etc.

You may find that something like Puppy-Linux is a better option if you really need to use it for anything important, though even that will be slow.

That's life, I'm afraid; technology moves on faster and faster and leaves old hardware behind!

---

