---
title: "PCManFM background colour in split view"
date: 2015-05-22
forum: General Help
---

### Post by OhLongCat on 2015-05-22
In PCManFM split view when one part/tab is inactive its background colour changes to very bright blue. Is there a way to change it to some other colour, say, light grey?

---

### Post by Dennis N on 2015-05-22
I can see the same if I use certain themes - Greybird, Clearlooks were two giving bright blue. I suggest you try a different theme. On my system, Lubuntu default gives a light grey for the unfocused split pane background, for example.

---

### Post by OhLongCat on 2015-05-22
I tried different themes, nothing changed.

---

### Post by Dennis N on 2015-05-22
When I looked at the supplied themes, the background changes were easy to see. If you see no changes, I'd suspect something is not right in what you did when changing themes. If you would give a step-by-step of what you did, someone here could possibly tell what you might be doing wrong. Otherwise, it is just a guessing game from this end.

---

### Post by vasa1 on 2015-05-23
> **Dennis N said:**
> I can see the same if I use certain themes - Greybird, Clearlooks were two giving bright blue. I suggest you try a different theme. On my system, Lubuntu default gives a light grey for the unfocused split pane background, for example.
@**Dennis N**, I played around a bit with my theme's *~/.themes/theme_name/gtk-2.0/gtkrc* and got the impression that the "unfocused split pane background" is related to **selected_bg_color** at least for my theme for which Greybird (from the shimmer-themes package) was the starting point. I'm using PCManFM 1.2.0.

To get the image below, I changed```
gtk-color-scheme	= "bg_color:#111111\nselected_bg_color:#333333\nbase_color:#050505" # Background, base.
```to```
gtk-color-scheme	= "bg_color:#111111\nselected_bg_color:maroon\nbase_color:#050505" # Background, base.
```

---

### Post by Dennis N on 2015-05-23
Yes, thanks for that. I can see it depends on the selected background color in your example, and so we have two examples to show themes can define this differently: Lubuntu-default doesn't use selected background color (as you may have already checked) for the pane; and as you proved, your Greybird does.

Lubuntu-default below:
[ATTACH=CONFIG]262151[/ATTACH]. 
Only thing I can fault here is the text color on the inactive tab.

And for the T.S., it would be a way to modify the pane background if his theme worked that way. Still no info on his inability to change themes, so this is at a standstill.

---

### Post by vasa1 on 2015-05-23
> **Dennis N said:**
> Yes, thanks for that. I can see it depends on the selected background color in your example, and so we have two examples to show themes can define this differently: Lubuntu-default doesn't use selected background color (as you may have already checked) for the pane; and as you proved, your Greybird does.
...
Good catch! But I admit I didn't check Lubuntu-default. Now that you pointed it out, I did check and I see what you see. Maybe the answer lies in **pcmanfm.rc** (in the gtk-2.0/assets folder)? 

```
style "treeview" {
	engine "clearlooks" {
		hint = "treeview"
	}
}

style "treeview_header" = "default" {
	xthickness = 2
	ythickness = 1
	engine "clearlooks" {
		hint = "treeview-header"
	}
}
```So, in addition to the murrine engine, Lubuntu-default also uses the "clearlooks" engine!

I think, though I'm not sure, that Greybird's gtk-2.0 is pure murrine.

---

### Post by vasa1 on 2015-05-24
> **Dennis N said:**
> ... 
Only thing I can fault here is the **text color** on the inactive tab.

And for the **T.S.**, ...
@Dennis N, 

1. I think that both Lubuntu-default and Greybird use **selected_fg_color** as the text color in the inactive pane's tab.

2. And is TS the same as OP?

---

### Post by Dennis N on 2015-05-24
I agree and think it is the selected foreground color - and it's a bit hard to read, but I would say it's relatively unimportant - seems to only affect tabs in the split pane view. If you use tabs with full windows in PCManFM with Lubuntu-default, the text on all tabs is black. So I will let it be.  There could be a section in the theme dealing specifically with these panes, but I haven't looked yet.

T.S. = Thread Starter

---

