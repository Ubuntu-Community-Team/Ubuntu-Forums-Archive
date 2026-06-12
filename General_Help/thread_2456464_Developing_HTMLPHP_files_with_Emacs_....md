---
title: "Developing HTML/PHP files with Emacs ..."
date: 2021-01-12
forum: General Help
---

### Post by dbee on 2021-01-12
Looking for emacs add-on that'll help with developing PHP/HTML files on a single page for WordPress platform.

html-mode doesn't seem to work for PHP pages. 

Need as much functionality as possible, including formatting, fuzzy selection etc...

---

### Post by dragonfly41 on 2021-01-12
[I have never used emacs]("https://www.quora.com/Why-do-great-programmers-use-Emacs-rather-than-Atom-or-Sublime-Text") .. I use [Atom]("https://atom.io/") and other tools such as Sublime Text 3.
But out of curiosity I explored how Atom and emacs might be configured in a cooperative toolchain.
These are the [emacs related packages]("https://atom.io/packages/search?q=emacs") available in Atom.
So in my thinking you could continue using emacs but pass certain tasks over to Atom (and vice versa).
Atom has PHP server package, markdown, snippets, autocomplete and other development tools.
You could argue that Atom is your emacs "add-on".

---

### Post by Holger_Gehrke on 2021-01-12
On my system Emacs has a php-mode which emacs runs in if I visit a file with the extension .php or .phtml. I can also start it manually with 'M-x php-mode'. I can't recall having done anything to install it but doing an 'apt search emacs' and searching for php in the result shows that there's a package named 'php-elisp' installed.
It even has a function php-mode-enable-wordpress-coding-style to support coding for wordpress.

Holger

---

### Post by SeijiSensei on 2021-01-12
I've used the Emacs clone [jed]("https://www.jedsoft.org/jed/") for many years now. It also has syntax highlighting and other goodies for PHP code. jed is in the Ubuntu repositories.

Having an editor that keeps track of open braces, parentheses, etc., is worth its weight in gold.

---

### Post by dbee on 2021-01-27
thanks Holger,

I've installed php-mode and it seems to be working fine. that's going to save me some serious hassle in the future.

can't find any php-mode-enable-wordpress-coding-style though. Is that in the php-elisp library?

---

### Post by Holger_Gehrke on 2021-01-28
"php-enable-wordpress-coding-style" is an emacs lisp function in "/usr/share/emacs/site-lisp/php-elisp/php-mode.el". You can either hit M-x and enter the function name or - if you haven't changed the key bindings - hit "C-c ." and enter "wordpress" or you can select 'set style' from the 'Style' menu in the 'C' menu end enter "wordpress".

Holger

---

