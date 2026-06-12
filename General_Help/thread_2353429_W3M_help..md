---
title: "W3M help."
date: 2017-02-21
forum: General Help
---

### Post by Furycd001 on 2017-02-21
HI Guys.

I am trying to use W3M to show an image in a terminal session. I can get the image to show but I cannot get it to appear properly. The image for some reason overlaps the toolbar, though the toolbar is still fully functional. Please have a look at the image below which is a screenshot of my problem. This problem also happens with neofetch. Hope someone can help me fix my problem :-)

[IMG]http://i.imgur.com/bfSioaN.png[/IMG]

---

### Post by DuckHook on 2017-02-21
W3M is not designed to be used in a terminal session in graphics mode. It requires a true framebuffer which is only emulated (and rather poorly so) in gnome-terminal. If you switch to a proper TTY with <Ctrl>+<Alt>+<F1>, you will see that it displays correctly there. I'm surprised that you got any graphics output in gnome-terminal at all. I cannot do so using Links2, which is another CLI-based browser like W3M.

---

### Post by Furycd001 on 2017-02-22
Thank you very much for your reply :-)

---

### Post by DuckHook on 2017-02-22
No problem.

In future, as a courtesy to members with low bandwidth, please attach your images to your posts using the paperclip icon in the Advanced Reply typing box.

---

