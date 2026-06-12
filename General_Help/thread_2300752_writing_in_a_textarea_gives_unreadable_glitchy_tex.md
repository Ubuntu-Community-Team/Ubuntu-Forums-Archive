---
title: "writing in a textarea gives unreadable glitchy text"
date: 2015-10-28
forum: General Help
---

### Post by levdeux on 2015-10-28
Hi,
I was having a problem with text areas in firefox and wanted to ask for some suggestions here before submitting a bug report. There is a glitchy grey or black highlighting that appears over any text I put into a text area, and sometime the letters overlap with each other. The textarea is refreshed to a correct state when I click in the text area, mouse over the text area, or press enter in the textarea. The attached image shows the problem (the website used to generate the example is [here]("http://www.w3schools.com/tags/tryit.asp?filename=tryhtml_textarea")):

[IMG]http://i.imgur.com/rirysJo.png?1[/IMG]

I am running firefox build 41.0.2+build2-0ubuntu1 with Ubuntu 15.10 and the Gnome-Flashback Desktop on amd64. Any suggestions? 
Thanks

---

### Post by vasa1 on 2015-10-28
Some suggestions:
try in safe mode or with a new profile (no added extensions) or another gtk theme? If you've already done so, it maybe worth mentioning in the original post itself.

---

### Post by levdeux on 2015-10-28
I did not think to change the theme. it looks like the problem only happens with the Adawaita theme, which I was using. Switching to Ambiance eliminates the problem. Thank you! Any ideas for where to proceed from here, if I wanted to continue using Adawaita?

---

### Post by vasa1 on 2015-10-28
> **levdeux said:**
> I did not think to change the theme. it looks like the problem only happens with the Adawaita theme, which I was using. Switching to Ambiance eliminates the problem. Thank you! Any ideas for where to proceed from here, if I wanted to continue using Adawaita?
Sorry, but I don't know. The last time I looked at Adwaita, a couple of years ago, it seemed pretty difficult to "deconstruct".

---

