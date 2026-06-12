---
title: "Nautilus/Files &amp; Bookmarks/Starred?"
date: 2020-07-21
forum: General Help
---

### Post by 2CV67 on 2020-07-21
Hi!
In trying to find a convenient way to launch my frequently-used files in Ubuntu 20.04 (since Drawers no longer works) I wondered if I could use Nautilus (now called Files?)

My first idea was to use Bookmarks but I couldn't find how to add any new Boomarks, even though some of my old Bookmarks are still present.
Have Bookmarks gone?

My second idea was to use the "Starred" category in the left panel.
But I only seem to be able to Star items which are directly under the Home folder, not the 99.9% of items which are in sub-folders.
Is that right?

Are there any instructions anywhere about using Bookmarks & Starred items in current Ubuntu?
I found lots of instructions for older versions which seem to no longer apply...

Thanks for any help!

Note: I have another thread asking about Drawers, but this one is specifically about Nautilus, so better kept separate, I think.

---

### Post by #&amp;thj^% on 2020-07-21
I wonder if something like this would be viable for you?
Put the ".desktop entry" in "/home/USERNAME/.local/share/applications"
Now it is shown (with the given icon) if you hit the “Show Applications” (bottom-left corner).
right click the icon and select “Add to favorites”. Just not sure how well that would work for just Files though.

---

### Post by Dennis N on 2020-07-21
> My first idea was to use Bookmarks but I couldn't find how to add any new Boomarks, even though some of my old Bookmarks are still present.
Have Bookmarks gone?

_Bookmarks_
They haven't gone. You can bookmark folders, but not files. Add by right-click on the pathtile for the folder in Files. See attached screenshot.
_Favorite File Access_
Try: Gnome Shell Extension "Files View"

---

### Post by 2CV67 on 2020-07-22
> **Dennis N said:**
> _Bookmarks_
They haven't gone. You can bookmark folders, but not files. Add by right-click on the pathtile for the folder in Files. See attached screenshot.
_Favorite File Access_
Try: Gnome Shell Extension "Files View"

Thanks very much - Files View seems to do just what I wanted!
I can pin any file or folder in the "Favorites" area.
I can access Files View Favorites in one click from the panel.
I can launch any Favorite in one simple click.
Files View closes automatically.

Really the same behaviour as Drawers.

Thanks again!

---

### Post by 2CV67 on 2020-07-22
NOT important but, with Files View, is there a way to change the order of items in the "Favorites" view?

They seem to stay in the order they were introduced & I didn't see any way to readjust them.

This is just a minor convenience question.

---

### Post by Dennis N on 2020-07-22
> NOT important but, with Files View, is there a way to change the order of items in the "Favorites" view?

There are sorting options in the preferences, but like you, I don't see those preferences being followed with the Favorites. They are just shown in the order added.

---

