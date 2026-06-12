---
title: "Ran out of disk space in crouton chroot on Chromebook"
date: 2015-10-05
forum: General Help
---

### Post by Philip_Hoskins on 2015-10-05
[FONT=Helvetica Neue]I'm running a crouton chroot of ubuntu on a chromebook, and I accidentally used up all my disk space by installing texlive 2015. Oops. Is there a way I can delete it from the chrome console?[/FONT]
[FONT=Helvetica Neue]Alternatively, and this is likely easier, I would be happy to just wipe everything and start over, provided I can recover some files that were written to the hard drive while in the chroot.[/FONT]
[FONT=Helvetica Neue]I hope I explained that right, I'm still new to GNU/Linux, so please feel free to ask me to clarify.[/FONT]

---

### Post by Philip_Hoskins on 2015-10-06
It ended up being a simple fix. I was able to find the texlive folders in crosh and delete them. This freed up enough space to run startkde and from there I was able to restore everything to its previous state.

---

