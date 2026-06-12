---
title: "Typing on wallpaper?"
date: 2008-03-06
forum: General Help
---

### Post by crhis on 2008-03-06
I was wondering if there was an application or a way to be able to type on wallpaper, kinda like stickies but without a background and cover the whole page. Or if the text could always be above all other windows. Something like that. Just alt click or shift alt click, some combination of clicking and keys, in an open part of the desktop or something. Not urgent, just kinda curious

---

### Post by tszanon on 2008-03-07
The most similar thing I know is that compiz-fusion plugin that allows you to draw on the screen with the mouse (holding Alt+Super and dragging the mouse). But, as I said, you can't type - just draw. And it stays on the foreground, above everything else, including the screensaver, until you erase it all (Alt+Super+K).

I guess it doesn't fit your needs.

---

### Post by strider1551 on 2008-03-08
I was looking for something like this the other day.  The best I could come up with was using conky to output the content of a file.  If you are familiar with ~/.conkyrc, I simply added the following:

```
${execi 3600 cat ~/todo }
```

If nothing else, conky at least demonstrates that it is possible to write text on the background.  If you know whatever language conky was written in, you could probably sift through the source...

---

