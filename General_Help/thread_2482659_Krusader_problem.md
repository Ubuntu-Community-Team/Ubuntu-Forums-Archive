---
title: "Krusader problem"
date: 2023-01-07
forum: General Help
---

### Post by Lappert on 2023-01-07
I've been using an older version of Krusader File Manager (v 2.4.0-beta3) for many years. This is on a box with Kubuntu 15.10. Yes, I know, that's ancient and I am in process of building a new box, but I don't think this problem relates to the age of either. Even with the age, for the most part, the system works well.

The problem I am having is in the left pane of Krusader. If I'm in a top-level directory (A) and click on a sub-folder (B), instead of just opening up the subfolder (B) and its contents in the same tab, it opens a new tab. The new tab is for the requested sub-folder (B), but in no time, I end up having a row of many tabs across the bottom.

On the right pane, if I'm in the same top-level directory (A) and click on the same sub-folder (B), instead of opening a new tab, the requested sub-folder opens in the same tab. I keep several tabs open on a permanent basis as I'm always using them. On the left, with all the new tabs that open up, it's a complete mess. The right side works like it should.

I've never seen this behavior until recently in Krusader, or in the old days with Windows Commander or even Norton Commander. Why would the behavior differ between the left and right panes?

I've gone through all the preferences and configurations and can't find anything that would create this issue, or fix it. As far as I can tell, the settings for the left and right panes are identical.

I will appreciate any suggestions on a fix. Thank you.

---

### Post by dragonfly41 on 2023-01-07
I am a fan of Krusader which I use daily for all my workflows.
I have version 2.7.2 on Ubuntu 20.04, so I cannot help with troubleshooting your earlier version.
My version does open subfolder in same tab in  either panel.
But if perhaps you right click on any folder do you see the menu ..
Open
Open in New Tab
Open With
and other options ...


Can you use ... Select Folder > right click > Open .. until you upgrade your desktop?

Or does this workflow open a new tab as you explain?

[P.S.] In my Krusader there is toolbar > Window > Swap panels and Swap sides.
This might help in troubleshooting.

---

### Post by Lappert on 2023-01-07
Dragonfly41,

Thanks for your reply. Yes, when I click on a folder, the menu options show up. However, Open and Open in a New Tab both do the same thing ... they both open in a new tab. I'll take a look at the Swap panels and sides.

Although bothersome, I can live with it until my new box is done (might be a few months as I take my time with research). Looking for the right mobo to match the i7-12700K CPU. Prefer the mid-to-high end, but not super gamer.

Appreciate your help. Thanks.

---

### Post by dragonfly41 on 2023-01-07
My thought was if you have your issue in left panel, with right panel working, does the"Swap Panels" option actually swap the symptoms?

I also use useractions feature for different workflows.

---

### Post by Lappert on 2023-01-07
With **Swap Panels**, the left and right panes should switch sides. Everything should switches, along with all the open tabs. So if you have on the left, tabs A, B and C, and then on the right you have tabs X, Y and Z, invoking Swap Panels will move ABC to the right side and XYZ to the left.

At least that is how it should work. What I see now is something strange, I don't know how to describe it. I think what happens is that the current tabs switch left and right, but not all tabs in each pane.
So if you had ABC tabs on the left and XYZ on the right, after Swap Panels, you would have AYC and XBZ ... only the B and Y tabs switched. I'm not sure waht value that might have, but I'm sure someone uses it.

Now, if I invoke **Swap Sides**, it looks as if the entire pane switches sides.

And to answer your question, after invoking Swap Sides, yes, the symptom now appears on the other side. I've thought the problem had to do with a setting tied to the pane ... but I can't find what it is. Or maybe it's just a bug :(

Maybe I should go back to sleep. Thanks again.

---

### Post by dragonfly41 on 2023-01-07
At least you now have another clue .. it is not panel dependent but travels when you swap panels.
Strange bug. Can you not go to Help > Report bug?

---

### Post by Lappert on 2023-01-07
You're right, at least it gets me a bit closer.

It could be a bug, but I'm not 100% convinced. I don't recall seeing this when I first started using Krusader (when I switched from Windows to Linux 8 years ago). Hard to say when it first appeared.

Plus, would they really work on a version from that long ago? The answer, of course, is to upgrade, which I'll do eventually.

Thanks.

---

