---
title: "xemacs dired"
date: 2008-01-07
forum: General Help
---

### Post by Pierre Imbaud on 2008-01-07
Ubuntu station 7.04, xemacs 21.4
dired doesnt work the way it should.
The dired buffer gets polluted by entries like:
//DIRED// 64 65 117 131 183 199 251 268 ...3
//DIRED-OPTIONS// --quoting-style=literal
saving file, especially Automated savings, fail every 2nd time
(pointing dired as the trouble source).
I can work though, but this is painful...
The same occured on other installs, by other guys, so this aint
a specific error.
Im newbie on Ubuntu (previously SUsE, redhat), and on debian.
long search on this on google, yielded nothing. (search on this forum too, btw!)
ideas, someone? Thanks a lot.

---

### Post by Jared Oberhaus on 2008-01-24
This is a bug and is reported in Debian's database:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=399483](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=399483)

If you follow the instructions at the bottom of the bug report, it seems to fix it...

---

### Post by Jared Oberhaus on 2008-02-01
From the above mentioned post, you should add this to your .emacs (or .xemacs/init.el):

```
(add-hook 'dired-load-hook
  (lambda ()
    (set-variable 'dired-use-ls-dired
      (and (string-match "gnu" system-configuration)
           ;; Only supported for XEmacs >= 21.5 and GNU Emacs >= 21.4 (I think)
           (if (featurep 'xemacs)
               (and
		(fboundp 'emacs-version>=)
		(emacs-version>= 21 5))
             (and (boundp 'emacs-major-version)
                  (boundp 'emacs-minor-version)
                  (or (> emacs-major-version 21)
                      (and (= emacs-major-version 21)
                           (>= emacs-minor-version 4)))))))))

```

---

