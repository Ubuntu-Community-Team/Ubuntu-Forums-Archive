---
title: "Alternative To VNC?"
date: 2008-01-18
forum: General Help
---

### Post by lonegeek on 2008-01-18
I've got vnc running on this computer(ubuntu), but when accessing with osx; it is painfully slow. This is all on a 100mbs wired network, so I feel like there should be something better. Is there something faster?

---

### Post by bodhi.zazen on 2008-01-18
Well, ssh is faster.

If you need the entire desktop, try FreeNX

---

### Post by HermanAB on 2008-01-18
Here you go:
$ ssh -X -c blowfish username@servername gnome-panel

Cheers,

Herman

---

### Post by lonegeek on 2008-01-19
> **HermanAB said:**
> Here you go:
$ ssh -X -c blowfish username@servername gnome-panel

Cheers,

Herman

I tried that and it just said

cannot open display: 
Run 'gnome-panel --help' to see a full list of available command line options.

---

