---
title: "Window Border Issues"
date: 2017-02-14
forum: General Help
---

### Post by mhaggard25 on 2017-02-14
So, I'm running Ubuntu Mate 14.04 and I've recently been experiencing a few issues. I have for some reason started having two different window boarders on some applications. What I mean by that is that, for example, in Chromium the window border is the correct one for what I've chosen. Then I open up gedit and the window border is different. I didn't ask for it to be, but now it is just different. There is an attached file that shows what I mean in case my explanation isn't clear. I don't really know how else to explain it. If more information is necessary, just ask for it. I don't even know where to begin looking to see why this problem occurred.

---

### Post by vasa1 on 2017-02-14
I think that gedit, being a gtk3 application, is using something called [client-side decorations]("http://stackoverflow.com/questions/28650646/what-is-client-side-decoration") which means that the developers of gedit decide how the "decorations" (title bar mainly) look.

Chromium browser isn't a gtk3 app.

Please search the internet for **turn off client-side decorations** for more information.

---

### Post by mhaggard25 on 2017-02-15
That worked perfectly. Thank you so much for your help and timely response. =d> I didn't even know that was a thing.

---

