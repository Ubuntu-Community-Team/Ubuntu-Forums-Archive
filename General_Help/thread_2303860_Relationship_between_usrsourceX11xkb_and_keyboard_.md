---
title: "Relationship between /usr/source/X11/xkb and keyboard layouts in the GUI"
date: 2015-11-22
forum: General Help
---

### Post by tupsharru on 2015-11-22
I am migrating from Windows 7 to Ubuntu 14.04 with Gnome shell.  I have a short list of software which I need to install or find substitutes for.  One of them is my custom keyboard layout for transcribing ancient near eastern languages, full of signs like á à &#7723; &#7717; &#7779; š.   It looks like the easiest thing to do is write a new layout for Linux using /usr/source/X11/symbols.  I have two questions about how the contents of that directory relate to the language settings in the GUI.

 First, how to I determine what file in /usr/source/X11/xkb/symbols is linked to each of the languages with two-letter abbreviations which appear at the top of Gnome or Unity and appear in Region & Languages &#8594; Input Sources (Gnome) or keyboard icon &#8594;Keyboard Layout Settings (Unity)?

 Second, how do I link a new keyboard in that folder to a new two-letter code in the GUI?  The Wiki page at [https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions#Editing_an_existing_layout](https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions#Editing_an_existing_layout) could be better written and is marked as needing to be updated for the current release.

 Its handy that both Unity and Gnome have that Windows+space shortcut for switching keyboard layouts!  That saves me a few minutes' work recreating the shortcut which I use on Windows boxes.  On the other hand, I am sad that the official online documentation requires people to enable several Javascript libraries from Google to make a simple search.

---

### Post by tupsharru on 2015-11-27
A friend introduced me to an alternative to memorizing Unicode numbers and creating a custom keyboard: Compose Keys [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)  Unfortunately the description in the Wiki only has about 3/4 of the characters I need, and I can't find a full description of the Gnome compose key table except this book [https://www.createspace.com/3758226](https://www.createspace.com/3758226)  So I would also be grateful to anyone who could point me to a complete description of the compose keys in Gnome.  If Gnome comes with a way to type aleph &#704; or theta &#952; with no more than three keystrokes, I don't want to reinvent the wheel.

---

