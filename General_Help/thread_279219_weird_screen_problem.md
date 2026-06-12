---
title: "weird screen problem"
date: 2006-10-17
forum: General Help
---

### Post by twidget on 2006-10-17
hi
I've got a weird problem. i had to switch my Kubuntu box down to a smaller monitor at work. now originally the screen went out of range so i had to switch down to a smaller resolution which is fine. however for some reason the computer thinks that the login screen should still be at the old resolution. i get a black screen until i type in my password and then kde loads normally. does anyone have any idea how i can fix it so that i can see my log on screen?

---

### Post by hopstah on 2006-10-17
edit your xorg.conf and look for something like ```
virtual (resolution)
``` under the ```
Section  "Screen"
``` section.

edit:  and comment that line out

---

