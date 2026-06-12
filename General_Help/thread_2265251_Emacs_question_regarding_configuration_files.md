---
title: "Emacs question regarding configuration files"
date: 2015-02-13
forum: General Help
---

### Post by jeremy46 on 2015-02-13
Hello.

I am trying to learn Emacs on my Ubuntu machine. Specifically, I would like to use Emacs as an editor for working with .php and .html files. Initially, I simply downloaded Emacs and started using it. I wanted PHP syntax highlighting, so I downloaded PHP-mode through apt. No configuration was required and the syntax highlighting worked right away. Unfortunately, various web discussions suggested that "web-mode" ([http://web-mode.org/](http://web-mode.org/)) was better suited to working with mixed php/html files. I read the instructions on the site and tried to install it through "melpa". It seems to have worked as I see a folder at ~/.emacs.d/elpa/web-mode-20150208.240.

This is where I get confused. I originally didn't have an .emacs file in my home folder, so I figured I had to create one when I needed to use melpa. Here is what it currently looks like:

```

(when (>= emacs-major-version 24)
         (require 'package)
         (package-initialize)
         (add-to-list 'package-archives '("melpa" . "http://melpa.milkbox.net/packages/") t)
         )
 
(require 'web-mode)
(add-to-list 'auto-mode-alist '("\\.phtml\\'" . web-mode))
(add-to-list 'auto-mode-alist '("\\.tpl\\.php\\'" . web-mode)
(add-to-list 'auto-mode-alist '("\\.[agj]sp\\'" . web-mode))
(add-to-list 'auto-mode-alist '("\\.as[cp]x\\'" . web-mode))
(add-to-list 'auto-mode-alist '("\\.erb\\'" . web-mode))
(add-to-list 'auto-mode-alist '("\\.mustache\\'" . web-mode))
(add-to-list 'auto-mode-alist '("\\.djhtml\\'" . web-mode))
(add-to-list 'auto-mode-alist '("\\.html?\\'" . web-mode))

```

Despite this, web-mode doesn't seem to be the mode that automatically loads when I try editing a php file. I'm no expert, but when I use "M-x describe-mode ENTER", I see information about PHP-mode so it seems that is still being used.

My first question is how is PHP-mode still configured to be the default for PHP files? Is there a configuration file for Emacs hiding somewhere that still points to PHP-mode? The only configuration file I can locate is my own .emacs file, which I manually created. My second question is how do I get web-mode to be the default for that list of file types?

Thanks for your help!

---

### Post by jeremy46 on 2015-02-15
I'm still working through this. I decided to try uninstalling PHP-Mode  through apt. I did this by running "sudo apt-get remove php-elisp".  After that, upon attempting to open a php file with emacs, I get this  error: "File mode specification error: (file-error "Cannot open load  file" "php-elisp/php-mo\de". To me, this certainly points to there being  another configuration file somewhere, which is why it is ignoring my  home .emacs file.

Any help would be greatly appreciated.

---

### Post by SeijiSensei on 2015-02-15
Try deleting the .emacs file and reinstalling PHP mode.  

Alternatively you can use [jed](http://www.jedsoft.org/jed/) which is in the repositories.  It provides an Emacs clone by default.  I've edited thousands of lines of mixed PHP/HTML code in it.  All the syntax highlighting was perfectly understandable.

---

