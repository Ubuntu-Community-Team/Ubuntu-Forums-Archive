---
title: "[SOLVED] Spellchecking with Kate in Xfce"
date: 2008-03-27
forum: General Help
---

### Post by Bruce M. on 2008-03-27
Hi folks,

I have kate installed in my Xfce 7.10.  I know I know, it's a KDE app, but it does some things I want and since I don't use a word processor I figured why not (ever opened a 464 page text file in a word processor, with a P-III@800MHtz ?).

However, it won't check the spelling. The popup says:
> The spelling program could not be started. Please make sure
you have set the correct spelling program and that it is
properly configured in your PATH.


Does anyone know what files I need to install to do that?

Thank for your trouble.
Bruce

---

### Post by -grubby on 2008-03-27
As far as I know Kate doesn't have a spell check function at all...it's a text editor, not a word processor. Well, if you can't get this to work somehow I'd recommend you use Abiword; a light word processor

---

### Post by Bruce M. on 2008-03-28
> **nathangrubb said:**
> As far as I know Kate doesn't have a spell check function at all...it's a text editor, not a word processor. Well, if you can't get this to work somehow I'd recommend you use Abiword; a light word processor

Did you even read what I wrote:

> **since I don't use a word processor I figured why not (ever opened a 464 page text file in a word processor, with a P-III@800MHtz ?).**

Also, if there is a pop-up that says:
> The spelling program could not be started. Please make sure
you have set the correct spelling program and that it is
properly configured in your PATH.
it's because I hit the Tools > Spelling button.

And since you are using GNOME open ***gedit*** and take a look at the very first command on the Tools Menu: **Spell Checking**!

---

### Post by mali2297 on 2008-03-28
Do you have **aspell** or **ispell** installed?

If not, install either of them together with a dictionary. For example, 
```

sudo apt-get install aspell-en

```
(the main aspell package will be installed as a dependency)

---

### Post by Bruce M. on 2008-03-28
> **mali2297 said:**
> Do you have **aspell** or **ispell** installed?

Installed: aspell, aspell-en, aspell-es

Not installed: ispell

Ok can it be that simple?

Be right back.

---

### Post by mali2297 on 2008-03-28
> **Bruce M. said:**
> Installed: aspell, aspell-en, aspell-es

Not installed: ispell

Ok can it be that simple?


No, ispell is just an alternative to aspell and shouldn't be needed.

I think you need **kate-plugins**. From the package description:
> 
This package contains a variety of useful plugins for Kate, the KDE Advanced Text Editor. These plugins can be loaded through the plugin manager in Kate settings.

Highlights include [color=blue]spell checking[/color], text filtering, HTML/XML construction and validation, vim/emacs modeline handling, templates for new files and text snippets, opening of C/C++ headers, extraction of C/C++ symbols, a tab bar, a Python browser and even more.

This package is part of KDE, as a component of the KDE addons module. See the 'kde' and 'kdeaddons' packages for more information.


---

### Post by Bruce M. on 2008-03-28
**Thank you mali2297**

I can now confirm that kate uses **ispell** and related word lists.

Again, thank you mali2297, have a great day.

Bruce

---

### Post by mali2297 on 2008-03-28
> **Bruce M. said:**
> **Thank you mali2297**

I can now confirm that kate uses **ispell** and related word lists.

Again, thank you mali2297, have a great day.

Bruce

So that others may benefit...

Did you simply solve the problem by replacing aspell with ispell? 

Or did you install kate-plugins as well?

---

### Post by Bruce M. on 2008-03-28
> **mali2297 said:**
> So that others may benefit...

Did you simply solve the problem by replacing aspell with ispell? 

Or did you install kate-plugins as well?

I installed kate-plugins when I installed kate, and had no spell check capabilities.

I installed ispell, and left aspell in place as other programs here use that I think, and now kate has spell check.

I'll do a test; and delete aspell and see what happens.

**EDIT:** Deleted aspell and found everything works just fine with ispell.  **Thanks again, mali2297**


Thanks
Bruce

---

