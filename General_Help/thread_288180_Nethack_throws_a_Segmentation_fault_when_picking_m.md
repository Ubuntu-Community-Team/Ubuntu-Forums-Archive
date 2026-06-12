---
title: "Nethack throws a Segmentation fault when picking my character. Kubuntu Edgy Eft."
date: 2006-10-29
forum: General Help
---

### Post by NickPresta on 2006-10-29
Hi,

Here is what happens:
1. $ nethack
2. Shall I pick a character's race, role, gender and alignment for you? [ynq] n
3. [List of character] *I press v* (end) Segmentation fault

This happened in Dapper Drake too. This is the version from the repo. Reinstalling does nothing.

Is there a problem with the repository version or am I missing something? I prefer not to compile this from source but if I have to, I will.

I tried searching on Google for an answer to this but nothing of value was returned.

Thank you for your time.

**EDIT:**
I just grabbed the binary (nethack-343-linux-X11.tgz) and I stil get a segmentation fault when trying to pick my character. I'll try to build from source.

**EDIT 2:**
I just want to mention that I have tried both the package "nethack-console" and "nethack-x11". Both produce the same problem.

---

### Post by potterzot on 2006-11-11
Found a solution on the bugzilla for ubuntu:

just open up a terminal and type:

export XLIB_SKIP_ARGB_VISUALS=1

here's the link:

[https://launchpad.net/distros/ubuntu/+source/nethack/+bug/55563](https://launchpad.net/distros/ubuntu/+source/nethack/+bug/55563)

---

