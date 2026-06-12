---
title: "Black Screen after Ctrl+Alt+F2"
date: 2008-04-09
forum: General Help
---

### Post by xelavonigol on 2008-04-09
Hello

I use Ubuntu Gutsy. The problem is that I cannot login to console after I push Ctrl+Alt+F2 (or +F1) buttons: I see black screen only, no console, no even blinking cursor. If I continuosly press 'Enter' - nothing happens. Ctrl+Alt+F7 brings me back to GDM. Crtl+Alt+Backspace works fine too. It is not related to my videodriver (I use Intel G33 chipset) because a few months ago everything worked fine.

I would appreciate any help.

Thanks.

---

### Post by MrFSL on 2008-04-09
This question has been addressed and answered a few times. This has to do with blacklisting of frame-buffer drivers.

Here is one place this has been addressed: [http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962)

---

### Post by mali2297 on 2008-04-09
A comprehensive guide can be found here:
[http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)

---

### Post by xelavonigol on 2008-04-10
Thanks.

I checked those messages but I am not satisfied with the solution: I replaced 'intel' friver by 'vesa'. Now Ctrl+Alt+F2 works fine. However the fonts are quite strange. Morever, Ubuntu's splash is also disturbed. Why does it happen? I have another PC with the identical hardware. Everything works fine there with 'intel' driver. Moreover, my PC used to work fine too not so long time ago...

---

### Post by mali2297 on 2008-04-10
I don't know where it was suggested to change the Xorg driver to vesa?

Anyhow, this bug seems to have been fixed for Hardy, which will be released in just 14 days from now. Why not upgrade then?

---

### Post by MrFSL on 2008-04-10
> **xelavonigol said:**
> Thanks.

I checked those messages but I am not satisfied with the solution: I replaced 'intel' driver by 'vesa'. Now Ctrl+Alt+F2 works fine. However the fonts are quite strange. Morever, Ubuntu's splash is also disturbed. Why does it happen? I have another PC with the identical hardware. Everything works fine there with 'intel' driver. Moreover, my PC used to work fine too not so long time ago...

Not really the problem... here I will lay it out as best as I understand it:

[FrameBuffer]("http://en.wikipedia.org/wiki/Framebuffer") drivers have been disabled in Gutsy because they are buggy (especially when dealing with suspending or hibernating a computer). If you are trying to increase the screen size by (for instance) adding vga=791 to your grub menu file you are actually enabling a framebuffer driver (typically vesafb for intel). This module (or driver) is loaded along with your X driver (intel).

So here is what I suggest.
0) Backup your xorg.conf
1) Replace vesa with intel (put it back the way it was) and restart X (ctrl+alt+Backspace).
2) Bring up a virtual terminal (ctrl+alt+F1) - It should be blank again
3) Go back to your desktop (ctrl+alt+F7) 
4) Open a terminal and load framebuffer drivers (sudo modprobe vesafb)
5) Check that module loaded without problems (lsmod | grep -i vesafb)
6) Go back to a virtual terminal (ctrl+alt+F1) and it should be working.
7) Go back and reread the supplied links on how to edit initramfs and blacklisted modules.

Hope this helps

---

