---
title: "Desktop always freezes after some minutes."
date: 2014-03-29
forum: General Help
---

### Post by nor-bak on 2014-03-29
Ubuntu 13.10 out of the box.
Acer 5920G with modded BIOS 5920G_MXM_V3.WPH and 9600m GT.
Desktop stops responding.

History:
I'been using Ubuntu for some years on this laptops without major problems.

After fixing/baking defective 8600m gt three times decided to change it for a 9600m gt,

Flahsed bios with modded one.
Started Ubuntu, Works fine.
Changed to 9600m GT - desktop stops working in several ways after some minutes (1 to 5 maybe):
-black screen
-mouse and keyboard works but desktop doesn't, no reaction from icons, menus.  ¿Unity?
-...

Changed from privative NVIDIA driver (tested several of the avalable ones in Aditional drives tab) to noveau and problem is gone.  I would prefer to use the privative one if posible.

I've changed back and forward from privative to noveau several times with same effect.

I've never had that problem with the 8600m gt.

I've read it could be a bios problem, a unity problem, a nvidia driver problem... but no solution.

Thanks.
---
O.T.  Everything works fine under Vista and GPU runs stable at 50ºC (no heavy graphics load).

---

### Post by sudodus on 2014-03-29
Welcome to the Ubuntu Forums :-)

If the computer works well with the nouveau driver but not with the nvidia proprietary driver, I think it is bad cooperation between your graphics card and the proprietary driver.

I know that you cannot use the full potential of the nvidia card with nouveau, but I think it will be the best now. Maybe you can check once a month if there will be a new proprietary nvidia driver, that will work with your graphics card.

I'm writing this reply from a computer with the [older] nvidia GeForce GT 430 card, that works well with the proprietary driver NVIDIA 304.88

---

### Post by nor-bak on 2014-03-31
I've searched around...

I got the System BIOS from "here".
[http://forum.notebookreview.com/acer/575866-acer-mxm-bios-mods-discussion-x920g-vs-9600m-gt.html](http://forum.notebookreview.com/acer/575866-acer-mxm-bios-mods-discussion-x920g-vs-9600m-gt.html)

On the first post there a solution for a problem vey similar to mine.
[http://forum.notebookreview.com/acer/689405-aspire-5720g-vs-nvidia-geforce-9600m-gt-512mb-ddr3-2.html#post8898826](http://forum.notebookreview.com/acer/689405-aspire-5720g-vs-nvidia-geforce-9600m-gt-512mb-ddr3-2.html#post8898826)

The solution is a workaround for some kind of nvidia driver bug.  Change Video Bios.
Did it and now I'm using 304 driver.  Played a bit a game on wine, so far so good.

The problem was related to windows drivers but it was fixed by nvidia or it was not so important on windows (Vista), under linux it's not solver but the workaround, whatever it does works.

---

### Post by sudodus on 2014-04-01
Sometimes a workaround is [almost] as good as a solution. Congratulations :KS

---

