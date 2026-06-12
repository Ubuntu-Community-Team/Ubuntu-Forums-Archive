---
title: "Terminal and CSI (control sequence introducer)"
date: 2013-12-22
forum: General Help
---

### Post by Newbunto on 2013-12-22
The Terminal application appears to support only the 7-bit (2 character) CSI (ESC+"[") and not the 8-bit (1 character) CSI (0x9B).

Is there any way to control this?

It would appear to interact with UTF-8. With Character Encoding set to Unicode(UTF-8) the 1 character CSI comes out as a diamond containing a question mark. This is probably to be expected as the 1 character CSI may well be invalid UTF-8 or in any case incorrectly encoded. Sending a correctly UTF-8 encoded 1 character CSI (not that that is ever going to happen naturally in my environment) comes out as a box containing 009B. Changing the Character Encoding to Western (ISO-8859-1) avoids the need to UTF-8 encode but the 1 character CSI still comes out as a box containing 009B.

So it seems that the Terminal application just doesn't support the 1 character CSI. Am I missing some configuration/preferences somewhere?

For those not intimately familiar with this stuff, background reading

[http://en.wikipedia.org/wiki/Control_Sequence_Introducer#Sequence_elements](http://en.wikipedia.org/wiki/Control_Sequence_Introducer#Sequence_elements)

---

### Post by Newbunto on 2013-12-23
PS This is gnome-terminal.

There doesn't seem to be a way of setting the Character Encoding for a new terminal window either i.e. other than manually using Terminal/Set Character Encoding once the terminal has been created. Edit: PS Which is too late.

---

### Post by Newbunto on 2013-12-24
Actually it seems that the initial Character Encoding *can* be set - by creating a new profile and using [FONT=courier new]gconf-editor[/FONT] to add the "encoding" key (type String, value ISO-8859-1) to the profile.

Then I can do [FONT=courier new]gnome-terminal --window-with-profile=*profile-name*[/FONT] which seems to work, while leaving the encoding in the default profile as current (which for me is UTF-8 and what I want by default).

However that is very much the smaller part of the problem.

---

