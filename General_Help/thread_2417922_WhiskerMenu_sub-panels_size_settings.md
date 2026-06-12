---
title: "WhiskerMenu sub-panels size settings"
date: 2019-04-29
forum: General Help
---

### Post by likwidoxigen on 2019-04-29
I can't for the life of me figure out where the heck I would go to set the percentages or min-width for these sub-panels. I can't imagine that this is seen as desierable behavior or figure ow why the line between the two doesn't let me drag it back and forth. I can't find a setting that implies that it's specifically locked and i looked through the config files as well as settings editor and nothing. 

Anyone have a way to resolve this anoyance? I just want the full text to show up in the right column.
Picture explanation -> [https://imgur.com/a/JBx6eaN](https://imgur.com/a/JBx6eaN)
[IMG]https://i.imgur.com/lSPOcuS.png[/IMG]

---

### Post by Holger_Gehrke on 2019-04-29
The problem is that the width of the categories panel is taken from the width of its widest element with no extra space allotted for a scroll bar. As long as you don't have too many categories or you make the menu tall enough for all categories to be visible this is exactly right. But if a scroll bar is needed, its width is taken from the panel, not added to it.

A workaround would be to use some menu editor (menu-libre,alacarte) or directly edit the .desktop files to remove the doubled categories (Development, Graphics) which hopefully would make the list of categories short enough to fit.

Otherwise you would have to work out some CSS to put into ~/.config/gtk-3/gtk.css to add some right margin to that panel. The problem with that is finding the right selector(s) ...

Holger

---

### Post by likwidoxigen on 2019-05-01
Thank you!!!! That makes perfect sense. I kept getting stuck on the "width" issue rather than even considering it to be the scrollbar. Thanks so much I didn't even think to associate that with a theming solution.

Fix that just gives enough padding for the scrollbar:

#whiskermenu-window button {
	background-color: #404040;
	color: #ccc;
	margin-right:30px;
}
I should note that this is suspect because it's operating on the button container so you get padding next to your username, logout, settings etc. buttons as well. I did some playing around with gtk inspector and i can't find any more specific selectors to use and I'm willing to live with the consequences.

---

