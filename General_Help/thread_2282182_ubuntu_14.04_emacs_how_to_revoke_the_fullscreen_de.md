---
title: "ubuntu 14.04 emacs: how to revoke the fullscreen default?"
date: 2015-06-12
forum: General Help
---

### Post by eugene55 on 2015-06-12
I started using an xps 13 (3200x1800 screen) with Ubuntu 14.04/Unity.  I am new to Unity. The emacs version   24.3+1-2ubuntu1 starts  fullscreen (or, rather maximized size). I tried to set the frame size in .emacs:
 (set-frame-size (selected-frame) 30 10)
but as I type in the first character the emacs window jumps to the maximum size again. Is this feature somehow associated with Unity? I have not seen it elsewhere. Does anybody know how to get rid of this feature? Thanks...

---

### Post by ennob on 2015-07-25
I have exactly the same problem. Running Emacs 24.4.1 and Ubuntu 15.04 on a Dell XPS 13 (2015 model).

I tried using various command line switches; I played with default-frame-alist and initial-frame-alist; nothing seems to work.

---

### Post by PaulW2U on 2015-07-25
*Thread moved to **General Help**.*

---

### Post by ennob on 2015-07-25
I have fond a workaround that fixed the problem for now:

```
; Hack to avoid full screen window on startup...
(defun my:window-setup-hook ()
  (toggle-frame-maximized)
  (when window-system (set-frame-size (selected-frame) 40 25)))
(setq window-setup-hook 'my:window-setup-hook)
; Note: `setq', *not* `add-hook'.  This is needed because `paren.el'
; sets this to also nullify `blink-paren-function'.

```

---

