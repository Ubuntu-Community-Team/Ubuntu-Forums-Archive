---
title: "EMACS can't find theme"
date: 2024-11-05
forum: General Help
---

### Post by Acharn on 2024-11-05
I'm running emacs 29.3 on ubuntu 24.04. I've been trying to install several versions of .emacs.d/init.el. One problem is common to all of them:
```

Done previously: cd .emacs.d; mkdir themes; M-x package-install RET ubuntu-themes RET
Installed into .emacs.d/elpa/ubuntu-theme-20150805.1506, then copied ubuntu-theme-20150805.1506 into .emacs.d/themes

(add-to-list 'custom-theme-load-path "~/.emacs.d/themes")
(load-theme 'ubuntu-theme)

When I enter C-x C-e
Debugger entered--Lisp error: (error "Unable to find theme file for &#8216;ubuntu-theme&#8217;")
  error("Unable to find theme file for `%s'" ubuntu-theme)
  load-theme(ubuntu-theme)
  (progn (load-theme 'ubuntu-theme))
  elisp--eval-last-sexp(nil)
  eval-last-sexp(nil)
  funcall-interactively(eval-last-sexp nil)
  command-execute(eval-last-sexp)

```

I did this successfully six month ago, and later had a hard drive crash. I can't remember exactly what I did then, but I was successful, and I really like the aubergine background and the colors for syntax. Can anyone see what I'm doing wrong?

---

