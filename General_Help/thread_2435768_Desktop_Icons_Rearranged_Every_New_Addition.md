---
title: "Desktop Icons Rearranged Every New Addition"
date: 2020-01-25
forum: General Help
---

### Post by 2CV67 on 2020-01-25
Hi!

I have always saved temporary stuff to my desktop, so usually have quite a few icons there.
Up till now, they stayed where I put them.
Suddenly, every time I save a new item, some or all the others move to new positions.
I really don't want that.
I have no idea what might have caused it.
Recent changes include adding Gnome Extensions "Dash to Panel" & "New Mail Indicator" but the problem persists with them disabled.

Thanks for any suggestions!

EDIT 28 Jan 2020: I forgot to mention that icons get shuffled when one is deleted too...

---

### Post by vanadium on 2020-01-26
Is this happening on  19.10, 18.04 LTS or 18.04 Lubuntu?

---

### Post by 2CV67 on 2020-01-26
Problem is on 19.10

Sorry, I forgot to specify that!  :redface:

---

### Post by 2CV67 on 2020-01-26
I just went back & checked in 18.04LTS on the same PC.

New icons are saved, filling in columns from top to bottom (filling gaps if present) then next column to the right, etc.
Old icons are left exactly where I put them.

Just the way I remember it & just the way I want it!

Now, whatever happened with my 19.10?

---

### Post by 2CV67 on 2020-01-27
I have done some more digging.

I booted a previous kernel (5.0.0.38 left over from 19.04, instead of my current 5.3.0.26 which came with the upgrade to 19.10 recently).
This old kernel, running in 19.10 (I think!) has the problem of shuffling icons.

I downloaded & SHA-checked 19.10, put it on a live USB stick & tried that.
It had an intermediate behaviour.
It never shifted any icon I had manually positioned, but it randomly shuffled icons placed automatically via "Save-As" to desktop.
It generally kept all the icons top-left-ish but would randomly use 1,2 or 3 columns (not increasing progressively, but switching about!)

I ran 18.04.3LTS from another live USB stick & it behaved perfectly.
Never shifted any existing icon, whether manually or automatically positioned.
Added new icons from top left, going down first column, then second column etc.
Filled gaps from top to bottom before starting new column.
Exactly what you would expect.
Or at least; exactly what I would expect.

I think there is a new bug in 19.10.

Nobody else seeing this?

---

### Post by 2CV67 on 2020-01-28
I again tried comparing Live-USB versions of 19.10 & 18.04.3LTS.

This time, I successively added (save-as to desktop) 32 tiny LibO files, called 01, 02, etc in that order.

I took screenshots to illustrate the icon shuffling.

18.04.3 again acted perfectly.
Icons were added top to bottom in columns progressing left to right.
No icon moved once in place.

[ATTACH=CONFIG]284922[/ATTACH] [ATTACH=CONFIG]284923[/ATTACH]

19.10 was again a complete mess.
Existing icons were shuffled about at nearly every addition.
New columns were started before previous columns were full.
Very often, the number of columns DIMINISHED when new icons were added.
This is just a sample:

[ATTACH=CONFIG]284924[/ATTACH] [ATTACH=CONFIG]284925[/ATTACH] [ATTACH=CONFIG]284926[/ATTACH]

Last few screenshots in next post...>>

---

### Post by 2CV67 on 2020-01-28
Last few screenshots with 19.10:

[ATTACH=CONFIG]284927[/ATTACH] [ATTACH=CONFIG]284928[/ATTACH] [ATTACH=CONFIG]284929[/ATTACH] [ATTACH=CONFIG]284930[/ATTACH]

Surely it's not just me?

---

### Post by 2CV67 on 2020-01-29
I raised a Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1861280](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1861280)

---

