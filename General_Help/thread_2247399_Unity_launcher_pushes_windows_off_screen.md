---
title: "Unity launcher pushes windows off screen"
date: 2014-10-07
forum: General Help
---

### Post by David_Cundiff on 2014-10-07
Hello,

I've got a few applications I'm trying to adjust to properly handle the existence of the unity launcher. The problem is the screen space it takes up that most API's don't take into account. This causes windows to get pushed off the side of the screen when opening.

The app I'm currently debugging is nagstamon. It uses pygtk to draw windows. When you hover your mouse over a floating bar it opens a window. The problem is pygtk draws the window based on screen size and unity pushes it to the right hiding the scroll bar. I know I can hide unity and fix the problem, however, I'm trying to fix it against default installs since I figure I might not be the only person who runs into this.

My question is do I need to just add

if OS with unity launcher
  subtract unity pixel width from not full screen window

Or is there a cleaner way to get the actual available screen space from various graphics libraries when you know something will be pushing a window somewhere else?

Thanks,
Dave

---

