---
title: "Black screen at startup"
date: 2012-12-31
forum: General Help
---

### Post by joblafors on 2012-12-31
Hello.
I have 2 laptops, both are HP Pavilion G series G6 and G7.

I use G7 and installed Ubuntu 12.04 long time ago and always had this problem: When starting computer it will always have black screen, only way to log in is to press fn+f3 or fn+f2 (screen brightness buttons) or to close and open the lid - this way black screen goes away and I can log in. If PC goes to hibernate I get the same problem. Now I'm quite used to this and it doesn't bother me much.

Now I set up Lubuntu 12.10 on my other laptop (G6), it has the exact same problem, but only way to get rid of black screen is to close the lid - brightness buttons doesn't work anymore. And I have to do this to see log-in screen AND after log-in to see desktop. So now I have a problem, I'm planing to give this to my little sister, cant expect her to do this every time she needs to use her computer.

I googled this problem and find a fix:
add *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"* to grub.

On my laptop (G7) this worked, but my desktop has changed a bit - hard to describe, but it has a bad feel to it. Window previews are in really bad quality, cursor flickers a lot, my icon sizes are back to default, desktop start-up seems to be slower.

On other one (G6) now it's stuck on Lubuntu splash screen and doesn't seem to do anything. Removed "nomodeset" and it's back to normal.

What should I do to fix this ?
Thank you for any help.

---

