---
title: "emacs and python programming"
date: 2005-09-16
forum: General Help
---

### Post by flyingman on 2005-09-16
Hi, you all!

Just installed Ubuntu 5.04 and installed emacs from the automatic Ubuntu add/remove programs.

I can get color (font-lock-mode) in C files and Lisp, but not in Python files. I have installed everything under "Python programming language".

Below  is my .emacs file. I tried to remove the "nil" statement also without result.
I also added this code to the beginning without result:
(defun my-python-mode-hook ()
  (setq font-lock-keywords python-font-lock-keywords)
  (font-lock-mode 1))
(add-hook 'python-mode-hook 'my-python-mode-hook)


What should I do to get color in emacs when programming Python?


(custom-set-variables
  ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(case-fold-search t)
 '(current-language-environment "UTF-8")
 '(default-input-method "rfc1345")
 '(global-font-lock-mode t nil (font-lock))
 '(show-paren-mode t t)
 '(transient-mark-mode t))
(custom-set-faces
  ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 )

---

### Post by arnieboy on 2005-09-16
[QUOTE=flyingman]Hi, you all!

Just installed Ubuntu 5.04 and installed emacs from the automatic Ubuntu add/remove programs.

I can get color (font-lock-mode) in C files and Lisp, but not in Python files. I have installed everything under "Python programming language".

Below  is my .emacs file. I tried to remove the "nil" statement also without result.
I also added this code to the beginning without result:
(defun my-python-mode-hook ()
  (setq font-lock-keywords python-font-lock-keywords)
  (font-lock-mode 1))
(add-hook 'python-mode-hook 'my-python-mode-hook)


What should I do to get color in emacs when programming Python?


(custom-set-variables
  ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(case-fold-search t)
 '(current-language-environment "UTF-8")
 '(default-input-method "rfc1345")
 '(global-font-lock-mode t nil (font-lock))
 '(show-paren-mode t t)
 '(transient-mark-mode t))
(custom-set-faces
  ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 )[/QUOTE]
try the following:

```
0. emacs -q

1. M-! which ipython
   (just to make sure the expected ipython path is used)

2. C-x C-f ~/emacs/python-mode/python-mode.el 
   M-x eval-buffer

3. C-x C-f ~/emacs/python-mode/ipython.el
   M-x eval-buffer

4. M-: (require 'ipython)

5. M-x py-shell
```


If that doesn't produce the desired outcome, it would seem that there's
something wrong with python-mode.el or ipython-mode.el (unless you're emacs is
completely screwed, which seems unlikely).

---

### Post by flyingman on 2005-09-17
0. emacs -q
DONE!

1. M-! which ipython
   (just to make sure the expected ipython path is used)
When typing "which ipython" in the shell:
bjornart@flyingman:/$ which ipython
bjornart@flyingman:/$
When doing the command in emacs:
(Shell command failed with no output)



2. C-x C-f ~/emacs/python-mode/python-mode.el 
   M-x eval-buffer

Have tried to do a find and a locate on the dir python-mode, but it doesn't exist, even though everything under "Python Programming Language" in Synaptic is installed.


3. C-x C-f ~/emacs/python-mode/ipython.el
   M-x eval-buffer

Couldn't locate any file by  that name

4. M-: (require 'ipython)

5. M-x py-shell


bjornart@flyingman:/$ sudo apt-get install python-mode
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package python-mode
bjornart@flyingman:/$

Can't find the python-mode ??
Strange since every Python package have been iinstalled using the Syanptic Package Manager...

What can I do about this?

---

### Post by flyingman on 2005-09-17
As a matter of fact, I don't think apt-get is working properly.

sudo apt-get install xemacs
#could not find package

sudo apt-get install mozilla
#could not find package

I do wonder if there is something about my internet connection that makes apt-get not work...

---

### Post by arnieboy on 2005-09-17
[QUOTE=flyingman]As a matter of fact, I don't think apt-get is working properly.

sudo apt-get install xemacs
#could not find package

sudo apt-get install mozilla
#could not find package

I do wonder if there is something about my internet connection that makes apt-get not work...[/QUOTE]
please paste the contents of /etc/apt/sources.list

---

### Post by flyingman on 2005-09-18
HaHaHa!! :-) Got it (have a look below).

But how should us new Linux users know where that file is and what it is for? I mean, I couldn't find it in the Help files, nor on the Internet... /etc/apt/sources.listit 



Now I'm almost finished with the Syntax Highlighting setup. When I load a .py file, emacs says (Python) in the lower part of the window. However, there are still no colors, even though Syntax Highlighting under "Options" is highlighted. 
However if I untick it, then tick it again the colors appears on my Python code.
Perhaps this is something about my .emacs file?


(custom-set-variables
  ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(case-fold-search t)
 '(current-language-environment "UTF-8")
 '(default-input-method "rfc1345")
 '(font-lock-mode 1 t)
 '(global-font-lock-mode t nil (font-lock))
 '(setq font-lock-keywords t)
 '(show-paren-mode t t)
 '(transient-mark-mode t))
(custom-set-faces
  ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 )
;; Python
(autoload 'python-mode "python-mode" "Python editing mode." t)
(add-to-list 'auto-mode-alist '("\\.py$" . python-mode))
(add-to-list 'interpreter-mode-alist '("python" . python-mode))






deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by flyingman on 2005-09-18
update: It seems like everything is in order. Found a code snip while googling and added it to my .emacs file:

(custom-set-variables
  ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(case-fold-search t)
 '(current-language-environment "UTF-8")
 '(default-input-method "rfc1345")
 '(font-lock-mode 1 t)
 '(global-font-lock-mode t nil (font-lock))
 '(setq font-lock-keywords t)
 '(show-paren-mode t t)
 '(transient-mark-mode t))
(custom-set-faces
  ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 )
;; Python
;;(autoload 'python-mode "python-mode" "Python editing mode." t)
;;(add-to-list 'auto-mode-alist '("\\.py$" . python-mode))
;;(add-to-list 'interpreter-mode-alist '("python" . python-mode))
  (defun my-python-mode-hook ()
   (setq font-lock-keywords python-font-lock-keywords)
   (font-lock-mode 1))
     (add-hook 'python-mode-hook 'my-python-mode-hook)


Seems to be working now. 
Now I will start configuring Linux to go to sleep when I close my laptop (Dell Inspiron 9300)
Any ideas on that?

---

