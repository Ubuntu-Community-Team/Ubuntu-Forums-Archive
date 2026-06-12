---
title: "xcompmgr and pypanel"
date: 2008-05-15
forum: General Help
---

### Post by watchitman on 2008-05-15
I'm using Openbox with xcompmgr and pypanel. I like pypanel but unlike the other windows, it has no drop shadow. Is there a way to get a drop shadow on pypanel? On a side note, I notice pypanel uses fake transparency - is there a way to make it use real transparency?

---

### Post by watchitman on 2008-05-16
*bump*

---

### Post by jviscosi on 2008-05-16
I'm not at my Ubuntu machine, but I think that xcompmgr either by default or with a flag won't draw drop shadows on windows that are of type "dock".  If pypanel identifies itself as a dock, that might be preventing the shadow from being drawn on it.

I actually had the opposite problem, where xcompmgr was drawing unwanted shadows on fbpanel and on gDesklets, and I used [Devil's Pie]("http://burtonini.com/blog/computers/devilspie") to change the window types to "dock" to keep that from happening.  I don't use xcompmgr much anymore but I do still use Devil's Pie to control what happens to windows when they open.  I can't remember if it's in the repositories or not.  Anyway, you might be able to use that to change the window type of pypanel to something that'll get a dropshadow.

If I remember, I'll test it when I get home, as I do have pypanel installed.

---

### Post by watchitman on 2008-05-17
You're suggestion gave me an idea so I went into the pypanel script and changed it's window type from DOCK to NORMAL and I got shadows! Thanks for the suggestion. Now I have to figure out how to keep it from being moved accidentally. :)

---

### Post by jviscosi on 2008-05-17
> **watchitman said:**
> You're suggestion gave me an idea so I went into the pypanel script and changed it's window type from DOCK to NORMAL and I got shadows! Thanks for the suggestion. Now I have to figure out how to keep it from being moved accidentally. :)

Cool!  That's certainly easier than futzing with Devil's Pie ...  ;-)

---

