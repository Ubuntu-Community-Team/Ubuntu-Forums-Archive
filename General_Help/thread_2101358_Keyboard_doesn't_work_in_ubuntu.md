---
title: "Keyboard doesn't work in ubuntu"
date: 2013-01-04
forum: General Help
---

### Post by dez93_2000 on 2013-01-04
Hi. I've completely run out of ideas and am really hoping someone can help.

Both USB & PS/2 keyboards aren't recognised when logged into ubuntu but both work in grub and windows. The background is that the video driver got buggy and I got help from nvidia ([here]("https://devtalk.nvidia.com/default/topic/525877/linux/api-mismatch-means-ubuntu-can-t-boot-i-can-t-fix-i-please-help-/1")) and on these forums ([here]("http://ubuntuforums.org/showthread.php?t=2095897")). My assumption is that there's something buggy in the files:
etc/X11/xorg.conf
and
/usr/share/X11/xorg.conf.d

If I 'delete' these by renaming them, ubuntu should use defaults, but then then mouse doesn't work. No amount of reading of the ubuntu manpage ([here]("https://wiki.ubuntu.com/X/Config")) or the xorg help ([here]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html")) has solved the problem. I've tried:
hiding each file individually
hashing out the option: CoreKeyboard option
hashing out the keyboard bit so ubuntu uses defaults
and other stuff which i don't recall currently but may add in later.

I can log into ubuntu and use the on-screen keyboard option to do stuff, so i thought maybe the best thing would be to bute the bullet & upgrade, but it requires keyboard input which i can't do from the onscreen as the entry box is a focus-stealing overlay.

So: ideally, if anyone can think of what i should tweak or how i could set my xorg.conf to force the keyboard to work, or if there's another file somewhere which is being accessed and I should edit, please let me know. I'm happy staying with 12.05 for now I reckon.

Or if not:, if someone knows what I should type into the recovery boot command line to upgrade, that'd be great, or would you recommend using liveCD?

Thanks in advance
dez

---

### Post by dino99 on 2013-01-04
you does not need xorg.conf, as now the kernel directly deal with X

so remove xorg.conf
( boot in recovery mode if necessary)

---

### Post by dez93_2000 on 2013-01-04
problem then is that my mouse isn't recognised....!

Any thoughts? My assumption is that the keyboard ALSO isn't recognised without xorg.conf but the mouse is the most obvious bit...

---

### Post by dez93_2000 on 2013-01-04
gave up & upgraded to 12.10, and both keyboard & mouse are working.
unlike a number of other things but that's the nature of upgrading: one huge step forward, one million tiny reversible steps backwards.

---

