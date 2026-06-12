---
title: "Spacebar required to enter quots"
date: 2006-11-18
forum: General Help
---

### Post by rickmans on 2006-11-18
When I want to type a quot (') or a double quot (") I have to press the quot-button ;) and after I pressed it, I should hit the spacebar to let it appear, when not pressing the spacebar, but the quot-buttong, other characters appear (entering single quot twice: ´ entering double quot twice ¨

As keyboard model I have: Logitech Cordless Desktop Pro (alternate option2)
As keyboard layout I have US international.

How can I enable my keyboard to display the ' and the " directly without using the space bar.

---

### Post by rickmans on 2006-11-18
anyone?

---

### Post by nekr0z on 2006-11-18
US International is your problem here. This layout is designed to easily input letters like **ä** or **é**: you press the quote, then a, and get ä as a result. These letters are used in some European languages.

For the ordinary quote key behaviour you need to change layout from US International to pure US English.

---

### Post by rickmans on 2006-11-19
I tried to chage the keyboard layout, but whatever I tried it didn't seem to work. The solution I found was editting the xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

The line XkbVarian should be outcommented and than it works like in the old days ;).

---

