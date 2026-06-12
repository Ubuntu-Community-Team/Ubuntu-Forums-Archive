---
title: "Nautilus Side Pane has disappeared"
date: 2008-05-02
forum: General Help
---

### Post by benali72 on 2008-05-02
My Nautilus side pane has disappeared.

I go to VIEW -> SIDE PANE F9 and toggle it (checkmarked or not), but the Side Pane does not re-appear.

I also tried VIEW -> SET VIEW TO DEFAULTS but it doesn't re-materialize the Side Pane.

Any ideas?  I'd hate to de-install / re-install Nautilus just to fix this, but I really like the Side Pane.

Thank you!

---

### Post by Ziggy72 on 2008-05-02
I have no idea if this will help at all, but I suggest you do <Alt>F2 and then run gconf-editor. When you've done that, navigate to apps > nautilus > preferences. Scroll down and have a look at the side_pane entries and see if anything looks strange. In particular, ensure that 'start with sidebar' is checked. then have a look at nautilus > sidebar_panels > tree and see if 'show_only_directories' is checked. That's all I can suggest. Best of luck.:)

---

### Post by WakkiTabakki on 2008-05-02
This may be a longshot... But it has happened to me before...
If you accidentally click on the bar separating the two areas in nautilus, the side bar "collapses"/"minimizes"... It looks like it's disappeared but it's still there. 
If you move your mouse to the left edge of nautilus and click it should reappear (just to the right of the window edge...

/N

---

### Post by benali72 on 2008-05-02
Thank you so much, Ziggy72!

I went into Alt-F2 (gconf-editor), then -> apps -> nautilus -> preferences.

There I noticed that "sidebar-width" was set to 0 !

I changed it to 120.  

Now I get the side bar just fine... somehow it had got set to a 0 width.

Thank you both for your help!

---

### Post by chrisccoulson on 2008-05-02
> **benali72 said:**
> Now I get the side bar just fine... somehow it had got set to a 0 width.

It probably got set to 0 by you clicking and accidentally dragging it. I do it all the time!

---

### Post by WakkiTabakki on 2008-05-02
> **chrisccoulson said:**
> It probably got set to 0 by you clicking and accidentally dragging it. I do it all the time!

Ahhh, ok. Ziggy and mine were pretty much solution to the same problem, then... 
Actually you don't even have to drag the bar, just click on it and it "minimizes"... First time it happened it literally took me ages to get it back again... (think actually I solved that by upgrading from Hoary to Breezy :p). 

Maybe something for the usability department to evaluate...


/N

---

### Post by LordDelta on 2011-02-02
In case any else gets here, the way I did, also using gconf-editor and checking "sidebar_show_places_menu" will get your places/tree list view menu back in the sidebar.

---

