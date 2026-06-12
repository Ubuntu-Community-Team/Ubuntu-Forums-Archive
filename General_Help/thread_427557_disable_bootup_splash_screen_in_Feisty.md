---
title: "disable bootup splash screen in Feisty?"
date: 2007-04-29
forum: General Help
---

### Post by wordsmithereens on 2007-04-29
Hi all;

A small question ... 

Looking for a way to disable the splash screen in Feisty.  

In 6.10 I could disable it in Sessions through the boot  options, but that appears to be gone in 7.04.

Thanks!

Wordsmithereens :)

---

### Post by divague on 2007-04-29
In a terminal put:

$gconf-editor

it'll open a window, then go to apps->gnomer-session->option and uncheck the show_splash_screen option

---

### Post by wordsmithereens on 2007-04-29
Thank you. 

That's one more thing I learned today. 8-)

~wordsmithereens~

---

### Post by emarkay on 2007-04-30
Uh, why has the menu option been removed?

---

### Post by divague on 2007-05-03
You can also add gconf-editor to the applications menu using alacarte

---

