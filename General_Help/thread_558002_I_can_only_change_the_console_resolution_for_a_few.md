---
title: "I can only change the console resolution for a few seconds"
date: 2007-09-23
forum: General Help
---

### Post by Keyper7 on 2007-09-23
Hi,

At a first look this might seem "yet another changing console resolution thread", but
my problem is a little different and I didn't find anything about it in the forums.

I'm trying to change my console resolution by appending "vga=*" in the kernel parameters.
In particular, I'm using vga=1, which is the 80x50 mode.

The problem is, it works perfectly for a few seconds (small fonts, yay!), but after a few
seconds into the boot the console returns to its regular resolution, I don't know why.

When I try recovery mode, the boot prints the first boot log lines in the resolution I want,
but after some point it clears the screen and prints the next lines in the normal resolution.
Since it clears the screen, I can't see where exactly the change occurred, but it seems
it's always at the same point (seems like right after "checking initrams image" or something)

I have a HP Pavilion dv6258se with a Turion X2 and a GeForce Go 6150. I'm currently
running Feisty amd64 with a vanilla 2.6.22.6 kernel.

Any clue?

---

