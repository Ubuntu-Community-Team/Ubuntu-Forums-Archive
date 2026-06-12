---
title: "emacs problems after upgrading to 7.10"
date: 2007-10-24
forum: General Help
---

### Post by giovabal on 2007-10-24
I upgraded from feisty to gutsy, python syntax highlighting (and all the nice related stuff) isn't working any more.
I installed a custom mode (django-mode) and it stopped working too.

The distro upgrade brings emacs upgrade from v21 to v22.
I uninstalled everything emacs related. I manually deleted things that the automatic unistall didn't deleted.
Now, installing emacs21 alone, emacs22 alone and emacs21 + emacs22  bring no relief: python-mode isn't working. Or at least no syntax highlighting in *.py files.

Notice that pymacs and python-mode files are in /usr/share/emacs*/site-lisp/, where they are supposed to be.

Moreover, I placed django-mode.el in the right place (/usr/share/emacs*/site-lisp/): while all emacs versions are correctly reading .emacs file (custom colors works, by example), django-mode isn't working too.

Any hint?

---

### Post by giovabal on 2007-10-24
solved
I installed emacs21, emacs22, python-mode
I manually copied /usr/share/emacs21/site-lisp/python-mode to 
/usr/share/emacs22/site-lisp/python-mode

emacs22 now works with python-mode, emacs21 isn't, but I don't care too much

and don't forget to add
(set-variable 'inhibit-splash-screen "True")
to your .emacs file if you want to disable the annoying splash screen that's default in emacs22

---

### Post by dm215 on 2007-11-12
I've got a similar problem.  Mine is that no text highlighting works -- at all.  Still works in emacs21 (which is still on my system even though the installer said that it would be removed).  Here's my .emacs file:

(custom-set-variables
  ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(color-theme-selection "Midnight" nil (color-theme))
 '(speedbar-frame-parameters (quote ((minibuffer) (width . 20) (border-width . 0) (menu-bar-lines . 0) (tool-bar-lines . 0) (unsplittable . t) (set-background-color "black")))))
(custom-set-faces
  ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(background "blue")
 '(font-lock-builtin-face ((((class color) (background dark)) (:foreground "Turquoise"))))
 '(font-lock-comment-face ((t (:foreground "MediumAquamarine"))))
 '(font-lock-constant-face ((((class color) (background dark)) (:bold t :foreground "DarkOrchid"))))
 '(font-lock-doc-string-face ((t (:foreground "green2"))))
 '(font-lock-function-name-face ((t (:foreground "SkyBlue"))))
 '(font-lock-keyword-face ((t (:bold t :foreground "CornflowerBlue"))))
 '(font-lock-preprocessor-face ((t (:italic nil :foreground "CornFlowerBlue"))))
 '(font-lock-reference-face ((t (:foreground "DodgerBlue"))))
 '(font-lock-string-face ((t (:foreground "LimeGreen"))))
 '(font-lock-type-face ((t (:foreground "#9290ff"))))
 '(font-lock-variable-name-face ((t (:foreground "PaleGreen"))))
 '(font-lock-warning-face ((((class color) (background dark)) (:foreground "yellow" :background "red"))))
 '(highlight ((t (:background "CornflowerBlue"))))
 '(list-mode-item-selected ((t (:background "gold"))))
 '(makefile-space-face ((t (:background "wheat"))))
 '(modeline ((t (:background "Navy"))))
 '(paren-match ((t (:background "darkseagreen4"))))
 '(region ((t (:background "DarkSlateBlue"))))
 '(show-paren-match-face ((t (:foreground "black" :background "wheat"))))
 '(show-paren-mismatch-face ((((class color)) (:foreground "white" :background "red"))))
 '(speedbar-button-face ((((class color) (background dark)) (:foreground "green4"))))
 '(speedbar-directory-face ((((class color) (background dark)) (:foreground "khaki"))))
 '(speedbar-file-face ((((class color) (background dark)) (:foreground "cyan"))))
 '(speedbar-tag-face ((((class color) (background dark)) (:foreground "Springgreen"))))
 '(vhdl-speedbar-architecture-selected-face ((((class color) (background dark)) (:underline t :foreground "Blue"))))
 '(vhdl-speedbar-entity-face ((((class color) (background dark)) (:foreground "darkGreen"))))
 '(vhdl-speedbar-entity-selected-face ((((class color) (background dark)) (:underline t :foreground "darkGreen"))))
 '(vhdl-speedbar-package-face ((((class color) (background dark)) (:foreground "black"))))
 '(vhdl-speedbar-package-selected-face ((((class color) (background dark)) (:underline t :foreground "black"))))
 '(widget-field-face ((((class grayscale color) (background light)) (:background "DarkBlue")))))

---

### Post by Qaazim on 2007-11-12
At risk of derailing the discussion - I am not new to Ubuntu but I am new to Emacs. I was under the impression that normally the .emacs file was ~/.emacs. But, it is not in my Home at all - even with hidden files showing. Where did you find yours in Gutsy?

Thanks!

---

### Post by gabrielsaldana on 2007-12-03
Just create a .emacs file on your home directory if there is none. Emacs will find it and read all your customizations.

---

