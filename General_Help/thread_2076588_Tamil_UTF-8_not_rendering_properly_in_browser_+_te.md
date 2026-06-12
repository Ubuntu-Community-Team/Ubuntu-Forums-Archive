---
title: "Tamil UTF-8 not rendering properly in browser + terminals and so on"
date: 2012-10-26
forum: General Help
---

### Post by loganathanspr on 2012-10-26
Hi,

In Chrome, Tamil UTF8 is not rendering properly. But it works correctly in Firefox. The problem occurs usually when 'Consonant + Vowel' pair occurs, the correct display should combine the characters into one , but they are displayed separately in Chrome.  The same problem occurs in unix  terminals as well as  for ex: Tk widgets.

Do you know how to solve this?

---

### Post by dino99 on 2012-10-26
on which installation are you seeing such issue ? (gnome, kde, ...) and with witch DE (unity, gnome-shell, gnome-classic) ?

when you says "terminal" do you mean gnome-terminal or else ?
Chrome is not supported here, only chromium.

Be sure you have the required language-pack (s) installed (ttf-tamil-fonts), and correctly set into the System Settings Language menu.

if the problem persist, then report that issue:

ubuntu-bug ttf-tamil-fonts

---

### Post by loganathanspr on 2012-10-26
The installation is gnome and the terminal is gnome-terminal.

The browser is chromium (I thought I was correct). There is no problem with the display of unicode text in gedit. But the problem is with the terminal.

I have attached a new screenshot... The terminal display is impossible to understand though some characters are displayed correctly.



> **dino99 said:**
> on which installation are you seeing such issue ? (gnome, kde, ...) and with witch DE (unity, gnome-shell, gnome-classic) ?

when you says "terminal" do you mean gnome-terminal or else ?
Chrome is not supported here, only chromium.

Be sure you have the required language-pack (s) installed (ttf-tamil-fonts), and correctly set into the System Settings Language menu.

if the problem persist, then report that issue:

ubuntu-bug ttf-tamil-fonts

---

### Post by dino99 on 2012-10-26
so report the problem:

ubuntu-bug gnome-terminal

you will need to accept an launchpad account creation if you have not one yet

---

### Post by mcduck on 2012-10-26
> **loganathanspr said:**
> The installation is gnome and the terminal is gnome-terminal.

The browser is chromium (I thought I was correct). There is no problem with the display of unicode text in gedit. But the problem is with the terminal.

I have attached a new screenshot... The terminal display is impossible to understand though some characters are displayed correctly.

Command-line interfaces only support monospace typefaces (where each character uses equal width, for example monospace typeface uses same width for letters "I" and "O", even though "O" would take more horizontal space in normal typefaces). Any other kinds of typefaces will render incorrectly. And that is not a bug, but simply happens because command line works based on rows and columns of characters and that requires each row and column to be same height and width.

---

