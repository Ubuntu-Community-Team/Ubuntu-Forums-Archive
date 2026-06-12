---
title: "Latex &amp; local style files"
date: 2007-12-19
forum: General Help
---

### Post by jaybee99 on 2007-12-19
I'm new to Latex and need to use a custom sty file. I have tetex (base, bin, extra) installed and Lyx. I tried to follow the instructions [here]("https://help.ubuntu.com/community/LaTeX") but bash won't accept "~/latex/:" as an env var. It complains:

```
bash: ~/latex/:: No such file or directory
bash: ~/texmf/:: No such file or directory
```

I need know how to set up my environment so that eventually I can create a lyx file using my local sty file in the preamble:

```
\usepackage{StuS13}
```

Or can you tell me where the system sty files go, just so that I can get on with it? (I'm sure that's frowned upon, but I need to get on with this).

Thanks!

---

### Post by hugmenot on 2007-12-19
This line is found in /etc/texmf/texmf.d/05TeXMF.cnf:

```
TEXMFHOME = $HOME/texmf
```

This means that you shouldn't need to define it, it's a lready defined.

just drop your style file in there and remeber to run texhash inside. This registers all new files to be found by TeX.

---

### Post by jaybee99 on 2007-12-20
Thanks for your reply -- you're right, this was an issue with my use of the style and LyX, not the latex paths. 

Cheers,

---

