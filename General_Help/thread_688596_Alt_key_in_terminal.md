---
title: "Alt key in terminal"
date: 2008-02-05
forum: General Help
---

### Post by ggeometry on 2008-02-05
I have recently installed Ubuntu on my desktop, replacing Debian. I'm happy to join this community.

Anyway, I have set up OpenSSH and noticed that key combinations involving the Alt key would produce accents or umlauts over the characters; I have since figured out that adding the line 

```
set convert-meta on

```

in /etc/inputrc would bring it back to what I was used to. However, whenever I run emacs from that terminal (again, I'm ssh-ing into the box from a different computer), the Alt key is no longer recognized as a meta key, forcing me to use Esc. For example, the combination Alt+> would ordinarily bring me to the end of the document in emacs, but instead produces an A with a tilde; in fact, almost all key combinations involving Alt that I have tried produces that character.

Is this a problem with my emacs configuration, or my terminal? How would I go about changing the behavior? I do not need to input special characters, so I would like to keep my old Alt+whatever keybindings.
Thanks for any help.

---

### Post by denalilumma on 2008-06-18
Hi There,

  Are you using a Mac locally, by any chance?  If so, the terminal application that ships with the Mac mangles the alt / option key.  So, for example, if you try to run emacs from within terminal, and use the alt / option key, you won't get the result you want. 

  To change this so the 'alt / option' key sends 'meta', go to:

Terminal > Preferences > Settings > Keyboard

and select the 'Use option as meta key' checkbox at the bottom of the window.

  I hope that helps,

-Denali

---

