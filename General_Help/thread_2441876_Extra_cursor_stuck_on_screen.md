---
title: "Extra cursor stuck on screen"
date: 2020-04-27
forum: General Help
---

### Post by jrohde on 2020-04-27
Hi

I have installed 20.04 twice on the same PC, and each time I have an extra cursor that is stuck in the middle of the screen. How do I get rid of that?

Thanks
Jakob

---

### Post by HermanAB on 2020-04-27
That is a bad video device driver.

During installation, it uses a very simple generic device driver that works with anything.  It then installs a more fancy device driver, which in this case, doesn't work.

How to fix it? First you need to find out what hardware you got.

---

### Post by jrohde on 2020-04-28
Hi HermanAB

I'm using a Intel NUC8i7HVK Hades Canyon with a AMD "Radeon RX Vega M GH" GPU.

I have noticed that when I boot up, the place where the "extra" cursor is, is where the cursor happens to be when the GUI loads - it simply leaves an imprint.

/Jakob

---

