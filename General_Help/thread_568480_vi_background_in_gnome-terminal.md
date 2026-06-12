---
title: "vi background in gnome-terminal"
date: 2007-10-05
forum: General Help
---

### Post by zbot on 2007-10-05
Hi Folks,

I have never been able to figure this one out, so here it is:

I have set the background of the gnome-terminal to be transparent (30%).  When I open vim editor in the gnome-terminal, I have the same transparent background regardless of my .vimrc file.  How can I have a background for the gnome-terminal that is transparent (which I already have), but while vim is open have it with a black background? Is this possible?

Thanks,
-zbot

---

### Post by zbot on 2007-10-06
Found it:

In your ~/.vimrc add the line:

```
highlight Normal ctermbg=Black ctermfg=White
```

Cheers.

---

