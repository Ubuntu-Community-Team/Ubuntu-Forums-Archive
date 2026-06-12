---
title: "Stumped about framebuffers"
date: 2005-04-14
forum: General Help
---

### Post by Falc on 2005-04-14
Okay, I hope this is the right forum for this...

What I am trying to do: use a video player (vlc as the case may be, but I'm willing to try out others) to play video files without actually starting up an X server.

A short search on the net told me that framebuffers were the way to go, and vlc supports framebuffer output.

But, I don't seem to have any framebuffers active on the computer. And this is where the internet search got out of hand, because I have no clue how to enable framebuffers and I got too many possible answers.

From some places, I get the idea I'll need to recompile my kernel. Then I found this [Ubuntu Bugzilla entry](https://bugzilla.ubuntu.com/show_bug.cgi?id=1837) and now I'm thinking, hey, it's already compiled in my kernel (stock hoary), so I just need to find some way to turn the framebuffers on...

Help me out, please...

---

### Post by Nis on 2005-04-24
In /boot/grub/menu.lst add 'vga=792' to the end of a kernel line (the default one probably) and you should have a framebuffer on boot.  You might need to change the 792 to something else; 792 gives you a 1074x768x24 framebuffer.  I'm not sure of the numbers but you could always experiment.

---

