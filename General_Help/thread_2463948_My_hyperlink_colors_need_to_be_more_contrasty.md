---
title: "My hyperlink colors need to be more contrasty"
date: 2021-06-21
forum: General Help
---

### Post by sofasurfer on 2021-06-21
The colors of my hyperlinks are hard to tell apart. When I use a hyperlink its color is not distinct enough to tell from an unused hyperlink. I also have found a couple of websites that have a "page 1" "page 2", etc icon that is barely visible until I put my cursor on them, then they stand out a little better but still not too good. I can't find any info on changing these colors except by changing entire theme. I would prefer a graphical interface but don't mind if I need to edit a file...which file by the way?

---

### Post by Holger_Gehrke on 2021-06-22
The file is userContent.css in the chrome directory in your profile directory. The css-rules in this file override the built-in styles but are overridden by site specific styles unless marked with '!important'. Starting with Firefox 69 both this file and userChrome.css (for changing the appearance of the browser itself) are not read unless the setting 'toolkit.legacyUserProfileCustomizations.stylesheets' is set to 'true' in 'about:config'.

Holger

---

### Post by &amp;KyT$0P# on 2021-06-23
sofasurfer, what browser are you using?
Is this a general question, or is this only about specific sites?

If your question is general, and your browser is Firefox, then the answer is [FONT=Courier New][noparse]about:preferences[/noparse][/FONT] > General > Language and Appearance > "Colors..."

If it is about specific sites, and your browser is Firefox or something Chromium-based (Chrome, Chromium, Opera, Vivaldi, etc) then try [Stylus extension]("https://github.com/openstyles/stylus#releases").

---

### Post by sofasurfer on 2021-06-24
Preferences seems to be the solution  I needed. There is no excuse for me not finding that myself but I couldn't seem to find it. Thanks.

---

