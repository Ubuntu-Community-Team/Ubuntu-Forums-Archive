---
title: "Easiest way to install php-html mode for Emacs?"
date: 2021-06-18
forum: General Help
---

### Post by dbee on 2021-06-18
I'm on xubuntu. I want to install php-html mode for emacs.

So that my html/css/js/php will be properly highlighted.

What's the easiest way to do this?

Also, what's the easiest way to format my code in emacs? So that indentation is all regular and consistent.

I have indentation issues all the time, and find myself constantly fighting emacs with regards to where I want to indent code and where emacs thinks I should indent.

Love emacs BTW. So save me the *switch editor* suggestions...

---

### Post by Holger_Gehrke on 2021-06-18
For Ubuntu 20.4 and newer there's a package named 'elpa-php-mode' in the repositories which is reasonably close to current (version 1.22 for 20.04; current at MELPA is 1.24). 

You can also use the built-in package manager of emacs and add MELPA (Milkypostman’s Emacs Lisp Package Archive) as a source of packages in ~/.emacs by adding these lines before '(package-initialize) :
```

(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)

```
Next you should refresh the list of packages with 'M-x package-refresh-contents' and install php-mode with 'M-x package-install'.

There are some hints regarding configuration of emacs-mode at [https://github.com/emacs-php/php-mode#configuration](https://github.com/emacs-php/php-mode#configuration) including selecting one of several available coding styles. The width of tabs - if that is your problem - can be changed in "Options->Customize Emacs"

Holger

---

### Post by dbee on 2021-06-27
Thanks.

I don't have a ~/.emacs file Holger?

---

