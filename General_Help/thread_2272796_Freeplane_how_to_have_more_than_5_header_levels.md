---
title: "Freeplane: how to have more than 5 header levels?"
date: 2015-04-08
forum: General Help
---

### Post by Jenske on 2015-04-08
Freeplane (a very good mind mapping program) comes with 5 header levels: title, heading1, heading2, heading3 and heading4. This is very handy when exporting a mindmap to a word processor like LO Writer. So far so good, but I cannot find a way to have also heading5 etc.

Somewhere in the manual, Freeplane says that you CAN have more header levels, but I cannot find how. And of course: I want those headers to be inserted automatically, not having to manually select all level 5 nodes and giving them style "heading5" etc.

---

### Post by bapoumba on 2015-04-08
Define the style as you want it to be. Format > Manage styles > New style from selection > Give it a name. It wont appear under level 4 if you name it Level 5, but in the user defined styles. I did nto find a way to change the location in the drop down menu. Please see the screenshot where I created a level 5 style (just applying italics).

---

### Post by Jenske on 2015-04-08
Thanks. I did this, but (as you may also have noticed) the heading levels are *not* automatically applied when entering nodes "deeper" than level 4. I suppose that is because Freeplane considers "your" level5, level6 etc. to be custom.

---

### Post by bapoumba on 2015-04-09
Yeah, I could not move the custom style below the default ones in the Style manager..

---

### Post by Jenske on 2015-04-17
I found two kinds of workaround.
1 - One can use a conditional style that has "level number of node" in it. This way one can make e.g. heading 5 nodes in bold, heading 6 italic etc.
2 - Export the mindmap (fully stretched out) as a html-file => open this in LibreOffice Writer => select all text => change the numbering with something you like (e.g. bullets, numbers, ...) // unfortunately I've not yet been able to let LO Writer then change the tabbed headings with the appropriate style heading number.

But both "systems" aren't really solutions, there merely "steps on the way to a solution".

---

