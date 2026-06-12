---
title: "sed: replace hex values"
date: 2005-09-25
forum: General Help
---

### Post by mozz on 2005-09-25
Hi,

I try to replace hex values in a file with:

sed s/\x0A/\x0D/g file1 >file2

but it seems that the script doesn't find the x0A values (and because of this doesn't replace them throug the x0D's)
Has anyone an idea how to fix that?

Thanks a lot

---

### Post by Prof_Tanner on 2005-10-11
Your problem is sed is a text editor that works line by line like vi.

In -nix's the line terminator is a linefeed character, your \x0A character.  sed never see's your \x0A as you have observed.

Try using the tr command which works byte by byte and would see the \x0A character.

---

