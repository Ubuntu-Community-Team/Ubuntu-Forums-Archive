---
title: "Fullscreen in mplayer?"
date: 2005-07-15
forum: General Help
---

### Post by Kimm on 2005-07-15
I have noticed that th e fullscreen mode in mplayer doesnt seem to work anymore, this happend after my last install of Hoary. I remember clearly to have had mplayer run in fullscreen flawlessly but now that is gone.

When I press fullscreen in the popupmenu the window covers the entire screen, but it does not expand the video itselfe, so what I get is a very large purple frame around what I am trying to watch.

I have even tried compiling it from source but with no luck, the program still wount expand the media. I'll provide you with a screenshot later but I cant now as I am not by my computer :)

Can anyone help?

---

### Post by Kimm on 2005-07-15
Heres the screenshot, its farly large though:

[http://i.domaindlx.com/MrKimm/mplayer.png](http://i.domaindlx.com/MrKimm/mplayer.png)

the frame was acctually black today, dont ask me why, I dont know :-P

---

### Post by Caboto on 2005-07-15
Got the same problem some time ago... Just switched the video output driver from xv to gl2 (you could also try xv, x11, gl or gl2). Just use mplayer -vo help for a complete listing of the video output drivers and mplayer-vo xv to use it.

If one of the drivers work, you can put it in the ~/.mplayer/config file with vo=gl2.

---

### Post by Kimm on 2005-07-15
thank you, now it works ^^

---

