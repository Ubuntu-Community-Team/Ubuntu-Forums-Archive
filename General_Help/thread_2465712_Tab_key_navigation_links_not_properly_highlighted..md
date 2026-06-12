---
title: "Tab key navigation links not properly highlighted. Need fix"
date: 2021-08-09
forum: General Help
---

### Post by sofasurfer on 2021-08-09
When I use the tab key to move around a web page the links that the tab lands on are not highlighted or not noticeable. When using chrome browser the links are very distinct but when using firefox they are not and have never been. I have found info to suggest that I need to do some work  work with style sheets which means that I need to ask you to point me in the right direction to learn about this process. Or is this a system setting that I need to change or a file I need to edit? Just tell me what I need to study.

---

### Post by Holger_Gehrke on 2021-08-10
Sadly this is more dependent on the website than on the browser. Here on ubuntuforums.org I don't get any visible keyboard focus while for example on tagesschau.de (german news site) it works very well. [This page]("https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible") on MDN gives some of the details on what needs to be put in the css for a page for visible highlighting of the focus. You might want to write a userContent.css and put a rule for focus display in there.

Holger

---

