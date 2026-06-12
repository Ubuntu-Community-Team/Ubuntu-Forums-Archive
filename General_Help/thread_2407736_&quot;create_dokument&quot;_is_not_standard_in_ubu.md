---
title: "&quot;create dokument&quot; is not standard in ubuntu?"
date: 2018-12-08
forum: General Help
---

### Post by enzo1337 on 2018-12-08
hi! i fixed the issue with (nautilius) i believe? with these commands:      but to my question why isnt this as standard? i find it super super super strange, isnt ubuntu trying to become the windows competition?, i have both a server and my pc with ubuntu and both have the sam issue and its just blows my mind why it is like this, PLEASE can somebody explain?

touch ~/Templates/Text\ File.txt

or 2 commands depending)


[LIST=1]
[*][FONT=inherit]See if you have ~/Templates folder[SUP]2[/SUP]. Create one if it is missing using command:[/FONT]

mkdir ~/Templates
[*][FONT=inherit]Now create an empty file from command prompt:[SUP]1[/SUP][/FONT]
touch ~/Templates/Text\ File.txt
[/LIST]

---

### Post by Impavidus on 2018-12-08
> **enzo1337 said:**
> isnt ubuntu trying to become the windows competition?
No, Ubuntu is trying to create a good product for a niche market. If you want to be serious competition to Windows, you have to be similar to Windows, which is what most current Ubuntu users wouldn't like.

"Create document" allows you to use the file manager to create an empty file of a particular type (so not completely empty, but just headers etc., no actual content), then instruct the file manager to open it, which will in turn call some editor with the instruction to open this empty file. Nice if you want to use the file manager as the central piece of your operating system, but I don't see the point. But the functionality exists. You need a template in your templates directory for every file format you wish to create that way, there are zillions of different formats and you have to tell your file manager which application you wish to use for each of these file formats.

When I want to create a new document, I start a programme that can edit documents of that type, I write the contents, then save the file. I've no need for file managers.

---

### Post by QIII on 2018-12-08
Ubuntu is an OS.  It's not trying to do anything.

Canonical, LTD., distributes Ubuntu and Canonical is not trying to make Ubuntu into some sort of Windows competitor.  It's just making Ubuntu.

---

### Post by mc4man on 2018-12-08
This is what Gnome (nautilus) decided to get rid of some time ago. Ubuntu used to patch nautilus to provide the context menu item, as of recently the patch broke & no one cares enough to redo (non trivial matter to fix patch..

---

### Post by The Cog on 2018-12-09
Is this the kind of thing you're looking for? This is a screenshot of thunar, the default file manager with xfce but it can be installed on Ubuntu (sudo apt install thunar).

---

