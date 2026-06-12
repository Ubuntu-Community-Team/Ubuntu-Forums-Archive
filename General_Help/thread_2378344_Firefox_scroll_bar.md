---
title: "Firefox scroll bar"
date: 2017-11-22
forum: General Help
---

### Post by The Cog on 2017-11-22
I thought I'd give firefox another try after seeing good reports about v57 (I'be been using chromium for a long time). It seems pretty good apart from one persistent "paper cut" that drives be back to chromium every time: the scroll bar on the right hand side of the page. I always browse full-screen and with every other app I can think of, when I want to scroll quickly I just mouse over to the scroll bar handle on the right, click and hold with the mouse and then slide it up and down. You can't do that with firefox. Every time I try, the page just jumps all the way to the bottom. It turns out you have to move the cursor to the edge of the page and **then back off by one or more pixels** before clicking. The scrollbar handle is one pixel short of the edge of the screen. And that last pixel isn't passive, it jumps the screen around.

I haven't seen other people complain of this. Is it something peculiar to my configuration (I use Xubuntu)? Does anyone know of a way to get the scrolling handle to touch the edge of the screen?

---

### Post by JonPaul on 2017-11-22
Works fine with my Ubuntu Budgie 17.10 setup...

---

### Post by vasa1 on 2017-11-22
Please see if [https://askubuntu.com/a/774203](https://askubuntu.com/a/774203) helps.

---

### Post by The Cog on 2017-11-22
Good try, thanks, vasa1. That's not it, but you did set me thinking.

With some more experimenting, I just discovered that this problem only occurs when I set my desktop appearance to Clearlooks-Phenix. Any other appearance setting is OK. No wonder nobody else was complaining about it. Interestingly, in the Clearlooks-Phenix appearance, the scroll handle does actually touch the edge of the screen (I used a magnifier to see the pixels easily). The handle changes colour slightly when the cursor scrolls over it, but the colour changes back as the cursor reaches the very edge pixel.  

I'll just have to settle for a different appearance - probably Clearlooks.
Thanks for the help - I just needed a slightly different perspective on it.

---

### Post by vasa1 on 2017-11-22
From what I remember, Clearlooks isn't for gtk3. Has it changed to supporting gtk3 as well? Because that's what Firefox uses.

---

### Post by The Cog on 2017-11-22
I don't really know how you would tell. Clearlooks works, firefox works. I read that clearlooks-phenix is a GTK3 port of clearlooks, but they both seem to work on Xubuntu (apart from the above bug).

---

### Post by vasa1 on 2017-11-22
> **The Cog said:**
> I don't really know how you would tell. Clearlooks works, firefox works. I read that clearlooks-phenix is a GTK3 port of clearlooks, but they both seem to work on Xubuntu (apart from the above bug).
Does the Clearlooks folder in */usr/share/themes* have a gtk-3.0 folder in it?

---

### Post by The Cog on 2017-11-22
> **vasa1 said:**
> Does the Clearlooks folder in */usr/share/themes* have a gtk-3.0 folder in it?
No. Only a gtk2 folder.
Clearlooks-Phenix has gtk2, gtk3, metacity, openbox and xfwm4.

---

### Post by vasa1 on 2017-11-22
Then, it's possible that Firefox will use the fallback theme whatever that is. Years ago, that used to be Raleigh. In more recent versions of gtk3, it may be Adwaita which is now part of gtk3.

---

