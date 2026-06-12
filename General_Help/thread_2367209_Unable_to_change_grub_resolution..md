---
title: "Unable to change grub resolution."
date: 2017-07-27
forum: General Help
---

### Post by cecchinosniper on 2017-07-27
Hi everyone, I'm having problems changing the grub resolution. I tried using the gfx line in /etc/default/grub and putting it at 1920x1080 and doing sudo update-grub but no luck.
I also tried adding a line to 00_headers that was "gfxpayload=keep" but no luck here. I removed it since it didn't do anything.
Do anyone have any idea? I'm using nvidia drivers. I'm on a laptop that has an integrated graphics card (intel hd 530) and a dedicated nvidia 960m.

---

### Post by Futant on 2017-07-27
Hello, welcome to the forum! Have you tried [this](https://askubuntu.com/questions/127851/change-boot-screen-resolution#174920)? Looks like you might have missed a few steps.

---

