---
title: "Keyboard layout: Dead keys usually don't work"
date: 2008-06-16
forum: General Help
---

### Post by mssever on 2008-06-16
My preferred keyboard layout is USA International (AltGr dead keys). Right after configuring the layouts, I can use the dead keys to produce additional characters. For example, pressing <RightAlt>' then e produces é. But shortly after I've finished configuring my layouts and I'm doing something else, the above method stops working. The example key combination just mentioned produces e, not é. And the layout's precomposed characters, such as <RightAlt>5 for the Euro sign, produce nothing. What's going on here?

Additional information: This worked fine on my old laptop. My current machine is a Lenovo ThinkPad R61i, which does some other weird stuff with my keys. I used to use <Shift>CapsLock to switch between layouts. However, this machine still somewhat toggles CapsLock state on that combination and makes many problems. So I had to switch to using ScrollLock as my toggle key (finally, a use for that key!).

---

### Post by Pjotr123 on 2008-06-16
What's in /etc/X11/xorg.conf ?

In mine, the relevant part says:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

```

-edit-
Furthermore, I don't understand why you use the Alt_GR key (RightAlt), except for the euro sign &#8364;. Other dead keys are simply the quotation mark-key and then the e-key for ë , etc. etc. No Alt_Gr (RightAlt) for that.

---

### Post by mssever on 2008-06-16
> **Pjotr123 said:**
> What's in /etc/X11/xorg.conf ?
My xorg.conf: ```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
```I've been using Gnome's keyboard settings instead of editing xorg.conf. I wonder if the last line of your xorg.conf will do the trick. I'll have to try it when I get a chance to restart X.
> Furthermore, I don't understand why you use the Alt_GR key (RightAlt), except for the euro sign €. Other dead keys are simply the quotation mark-key and then the e-key for ë , etc. etc. No Alt_Gr (RightAlt) for that.
Hardy makes a new US international layout available--which I'm using--in which the quote key alone produces regular quotes and <RightAlt>quote is a dead key. For my purposes, that's much better, since I use quotes a whole lot more than accented characters.

---

### Post by mssever on 2008-06-16
> **mssever said:**
> I'll have to try it when I get a chance to restart X.
I tried it, but it didn't have any effect.

---

### Post by mssever on 2008-06-17
I think I tracked this down. I reported it as Launchpad [bug 240615]("https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/240615"). From the bug report:
[quote=bug 240615]When the Greek Extended or Polytonic keyboards are in the list of selected keyboard layouts, then dead keys don't work--even in unrelated layouts. I've tested this with both the US International (AltGr dead keys) and US Dvorak layouts. By "don't work," I mean that they produce no output themselves and don't influence other keystrokes. For example, <RightAlt>5 should produce € but it produces nothing. <RightAlt>' followed by e should produce é, but it instead produces e.
 EDIT: This is in Hardy.[/quote]

---

