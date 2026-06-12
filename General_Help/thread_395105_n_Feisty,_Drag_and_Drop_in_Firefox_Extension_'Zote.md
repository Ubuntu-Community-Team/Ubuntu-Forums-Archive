---
title: "n Feisty, Drag and Drop in Firefox Extension 'Zotero' is refused (works in Edgy)"
date: 2007-03-27
forum: General Help
---

### Post by vav on 2007-03-27
I've posted a bug about this:
[https://bugs.launchpad.net/ubuntu/+bug/97196](https://bugs.launchpad.net/ubuntu/+bug/97196)

but wanted to know if there's a workaround... since the bug is so specifiic it'll probably get ignored.

The Zotero extension ([www.zotero.org](www.zotero.org)) has a sql based file organization capability.
It allows classification (into tags) and organization (into hierarchy) of files (typically research articles).
The organization is done through drag and drop. This works perfectly in Edgy.
Since I upgraded to Fiesty, when I try to drag a file into the intended location, the location doesnt get highlighted (if it's a tag), and even if it gets highlighted (in case of another file), the drop is refused... when I release the mouse button, it shows an animation of the file going back to it's original location.:confused: 

While dragging it doesnt show a (circle with a line through it) icon to show a drag to that location is not possible...

Any help will be appreciated... I'm back to M$ Windoze until this is sorted out :mad: 
By the way, to anyone doing research, I would recommend Zotero...:guitar:  it's still in beta 3 or so, but very functional and I expect most issues to be solved by the next beta.

---

### Post by vav on 2007-04-06
Here's a confusing thing:

I have another computer with Feisty, in the same state as my laptop, and drag-drop works perfectly in that! So the problem seems to be with my machine... how do I figure out where it is and fix it?

---

### Post by Detonate on 2007-04-06
I don't use that extension, but I once had a similar problem with another program, and it was because I did not have permission to write to the folder I was trying to drop the file in.

---

### Post by vav on 2007-04-23
huh... I found that my /usr/bin/firefox still pointed to the 2.0 version that I had manually installed and not the 2.0.0.3. When I fixed that everything works fine.

---

