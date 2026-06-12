---
title: "Subline text backspace not working"
date: 2013-04-21
forum: General Help
---

### Post by songeriux on 2013-04-21
Hello,

I have installed lubuntu from wubi and transformed to ubuntu light style...

So I am a php programmer and i am using subline text 2 (from windows) for linux and the backspace key does not work on it. How to solve this madness?

---

### Post by songeriux on 2013-04-21
No help?!?!

Gedit v3 install ftp plugin??

---

### Post by Habitual on 2013-04-21
Did you check under Preferences > Key Bindings - User...?

---

### Post by songeriux on 2013-04-22
> **Habitual said:**
> Did you check under Preferences > Key Bindings - User...?

Yes I did.. Nonne bindings in user bindings.. I even did fresh install.. Reinstalled Lubuntu, same problem

---

### Post by Habitual on 2013-04-22
> **songeriux said:**
> Reinstalled Lubuntu, same problemWell, now you know that re-instaling an OS is not necessary. (Opinion: 99% of the time).
You want to 'reset" sublime text2's settings, I'd close st2 and then open  a terminal and type this:
```
mv ~/.config/sublime-text-2/ ~/.config/sublime-text-2.org

``` and then restart st2. Defaults. :)

Please let us know.

---

### Post by songeriux on 2013-04-22
> **Habitual said:**
> Well, now you know that re-instaling an OS is not necessary. (Opinion: 99% of the time).
You want to 'reset" sublime text2's settings, I'd close st2 and then open  a terminal and type this:
```
mv ~/.config/sublime-text-2/ ~/.config/sublime-text-2.org

``` and then restart st2. Defaults. :)

Please let us know.

Nothing changed... The keybindings are the same..

One more thing, When selecting text and using backspace works, but without selecting it doesnt

---

### Post by Habitual on 2013-04-22
I dunno then sorry.
you can reverse the mv using terminal using ```
mv ~/.config/sublime-text-2.org ~/.config/sublime-text-2
```

---

### Post by songeriux on 2013-04-23
:( On other Linux distros it work fine..

---

### Post by foxawy on 2014-03-17
in SubLime 2
go to Preferences - > Key Bindings - Default

Ctrl + F then search for ctrl+backspace

edit it to be just [backspace]

save it then ur good 2 go

---

