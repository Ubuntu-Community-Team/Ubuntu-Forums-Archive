---
title: "Firefox trouble displaying text"
date: 2020-06-09
forum: General Help
---

### Post by dougfir2 on 2020-06-09
I have an intermittent issue that in Firefox on 18.04 often text is not displayed. I found several references to this and the common guidance was to check your add ons, especially ad blockers.

Example of issue:
[ATTACH=CONFIG]286170[/ATTACH]

Also, over on an online textbook I'm working through here: [https://openstax.org/books/algebra-and-trigonometry/pages/1-5-factoring-polynomials](https://openstax.org/books/algebra-and-trigonometry/pages/1-5-factoring-polynomials)
[ATTACH=CONFIG]286171[/ATTACH]
Note how text are missing with whitespace showing instead.

Here are all my add-ons. I tried switching off every one of them and revisiting the textbook page but the issue persists.
[ATTACH=CONFIG]286172[/ATTACH]

In case it's relevant, I am unsure of which version of Firefox I am on because when I visit software center it doesn't say. Screen:
[ATTACH=CONFIG]286173[/ATTACH]

Does anyone know what my issue is here and how I can fix it?

---

### Post by Holger_Gehrke on 2020-06-09
You can find out the version number of your Firefox by selecting 'Help'->'About Firefox' from the menu.

The screenshot of the forum looks like a font problem, the messed up lines seem to consist of Unicode placeholders (squares with four hexadecimal digits); for some reason ff seems to use a font that does not contain the needed glyphs.

The blank places in the textbook page look like MathML to me when I look at them with the Inspector, on my system they get formatted with the 'DejaVu Math TeX Gyre' font even though there's no reference to that font in the CSS for the page (might be some kind of default for typesetting MathML).

Holger

---

### Post by Impavidus on 2020-06-09
If it's MathML it's probably using a slanted font. The messed-up lines in the screenshot of the forum should also be in slanted font. That could be a lead, but I'm not sure how to proceed from there. You could try reinstalling some fonts...

---

### Post by GhX6GZMB on 2020-06-09
First, you can list your installed fonts using sudo fc-list to check for anomalies.

That's a starting point, at least.

---

