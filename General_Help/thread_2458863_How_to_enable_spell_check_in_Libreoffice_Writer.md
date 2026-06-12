---
title: "How to enable spell check in Libreoffice Writer ?"
date: 2021-03-05
forum: General Help
---

### Post by linuxyogi on 2021-03-05
I Googled & found this >>>[https://www.libreofficehelp.com/enable-automatic-spelling-grammar-check-libreoffice-writer/](https://www.libreofficehelp.com/enable-automatic-spelling-grammar-check-libreoffice-writer/)
My settings look like this (please see attachment).
Despite the correct settings no spell check is taking place.
[ATTACH=CONFIG]288063[/ATTACH][URL="https://www.libreofficehelp.com/enable-automatic-spelling-grammar-check-libreoffice-writer/"]
[/URL](Click to enlarge)

Please tell me what's wrong.

---

### Post by CelticWarrior on 2021-03-05
What are the writing aids settings?

---

### Post by linuxyogi on 2021-03-05
> **CelticWarrior said:**
> What are the writing aids settings?


[ATTACH=CONFIG]288064[/ATTACH]
(Click to enlarge)

---

### Post by grahammechanical on 2021-03-05
Is it not Tools>Automatic Spell Checking? Or, Shift + F7?

It used to be on by default. I turned it off long ago because I was including words spelt with a different alphabet and I got fed up with the squiggly red line under so many words.

There is Tools>Autocorrect Options which I have never explored.

Regards

---

### Post by linuxyogi on 2021-03-05
> **grahammechanical said:**
> Is it not Tools>Automatic Spell Checking? Or, Shift + F7? 
Automatic spell checking is selected but it has no effect. Spell checking is not taking place.

---

### Post by Dennis N on 2021-03-05
For spell checking, you need **hunspell** to be installed. Check that it is. It's available for many languages.

---

### Post by linuxyogi on 2021-03-05
> **Dennis N said:**
> For spell checking, you need **hunspell** to be installed. Check that it is. It's available for many languages.

Just installed hunspell by doing
```
$ sudo apt install hunspell-en-us
```
Now spell check is working. Thanks a lot.

---

