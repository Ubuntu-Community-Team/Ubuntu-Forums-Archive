---
title: "Changing bar color"
date: 2015-04-28
forum: General Help
---

### Post by tim105 on 2015-04-28
Hi all!

I am not sure if this is the correct section to ask, but I would like to change the color of a bar.  Could you please tell me which file to modify?

Here is a screenshot of the bar I want modified:  (im thinking its an image and so it doesnt change , im using default-lubuntu theme.)

[ATTACH=CONFIG]261620[/ATTACH]

Thanks

---

### Post by Dennis N on 2015-04-28
There are two "bars" here, menubar and toolbar. The menubar contains the menu headings: File Edit View... Looks like that is what's involved in the second image of the terminal.

I have changed a menubar background by changing a line in the theme's **gtk-2.0/gtkrc** file.

Look for something starting with **style "menubar" =** 
like this: (copied from a change I once made):

```
style "menubar" = "dark"
{
	bg[NORMAL] = "#4d4d4d" 
}

```

This is from Albatross theme after the change was made, not Lubuntu default, but it should have a similar entry.

---

