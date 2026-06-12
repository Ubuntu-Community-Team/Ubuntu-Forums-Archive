---
title: "General System Performance"
date: 2007-01-04
forum: General Help
---

### Post by vbeav99 on 2007-01-04
I have been using Ubuntu for about 6 months now (Currently on Edgy) and have stayed on because of some things that are convenient for me. However, there are a few things which are very frustrating:

1. My computer seems very slow when I am on Ubuntu. I'm have plenty of hard drive space, 512 MB of RAM, AMD XP+ 2400, and with this hardware Windows XP runs very smoothly - folders open up immediatly. In Ubuntu, it takes a few seconds for a folder to open, about 10 seconds for an application such as Kaffeine to open, etc.

2. Dragging folder windows is very choppy. I remember installing Nvidia drivers when I first installed Ubuntu to get widescreen resolutions to work.

Is there anything I can do to improve these things?
Thanks

---

### Post by riven0 on 2007-01-04
That shouldn't be so. If anything, Ubuntu should be fastter than Windows. Usually these problems are networking related, but you didn't mention you had a problem with your internet connection. 

You can try to see if this makes a difference instead. Can't make any guarantees, but it works for some people:

1. Reboot the comp and hit escape to get to grub

2. Highlight your kernel selection and hit e 

3. Highlight the line that looks similar to this:

> kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single 

and hit e again. Now scroll to the end of the line and add in **noapic** so it looks like this:

> kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single noapic

Now hit Enter and you should get to the previous screen, then hit b to boot up.

---

### Post by vbeav99 on 2007-01-04
Wow, well that helped a lot. Everything is a lot faster now.

Thanks

---

