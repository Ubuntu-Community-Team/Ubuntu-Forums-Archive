---
title: "Gthumb editing menu items disabled"
date: 2008-01-19
forum: General Help
---

### Post by lemd on 2008-01-19
I use Gthumb on two computers (both have gutsy, one is amd64, the other x86).
On one machine (amd64) all the items in Gthumb's Image menu are disabled. Basically I cannot even crop an image. I'm wondering if anyone experienced something like this.

(I have write permission to the image, I tried the same images I can modify via gthumb on my other machine). I also tried the live CD, both 32 and 64 bits, and these menu items are not enabled). However, on my other machine I can use these image editing features. I've compared the installed packages (dpkg -l then diff, but did not find anything obvious).

Regards,
   - L

---

### Post by lemd on 2008-01-19
Problem seems to be solved :) But it may actually be a bug.

In order to get the image menu items to be enabled, one needs to have the image preview shown (View->Show/Hide->ImagePreview). I'm not sure what the two have to do with each other, but, for those who run into the same problem, this seems to solve it :)

-L

---

