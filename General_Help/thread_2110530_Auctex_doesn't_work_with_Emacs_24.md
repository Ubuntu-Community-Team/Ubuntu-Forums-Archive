---
title: "Auctex doesn't work with Emacs 24"
date: 2013-01-30
forum: General Help
---

### Post by TheHimself on 2013-01-30
I had emacs 23 with auctex and now installed emacs 24 from a ppa and then installed auctex from emacs package manager. However auctex does not show up when I open a TeX file. Here is the appropriate lines in my .emacs:
```

(add-to-list 'load-path "~/.emacs.d/auctex")
(load "auctex.el" nil t t)
(load "preview-latex.el" nil t t)
(add-hook 'LaTeX-mode-hook 'turn-on-auctex)
(autoload 'cdlatex-mode "cdlatex" "CDLaTeX Mode" t)
(autoload 'turn-on-cdlatex "cdlatex" "CDLaTeX Mode" nil)
(add-hook 'LaTeX-mode-hook 'turn-on-cdlatex)   ; with AUCTeX LaTeX mode

```

Strangely CDlatex works but not auctex.

---

### Post by phobeste on 2013-04-17
There are two ways to solve this, both realizing that the file that actually loads auctex is called "tex-site.el" and not "auctex.el"

First way:
```


(add-to-list 'load-path "~/.emacs.d/elpa/auctex-11.86")(load "tex-site.el" nil t t)
```

Same as what you did but with the correct file. 
Second way: just rename "~/.emacs.d/elpa/auctex-11.86/tex-site.el" to "~/.emacs.d/elpa/auctex-11.86/auctex.el" and EMACS and ELPA will now autoload it for you like it's supposed to. It's beyond me why this isn't done in the package already.

---

