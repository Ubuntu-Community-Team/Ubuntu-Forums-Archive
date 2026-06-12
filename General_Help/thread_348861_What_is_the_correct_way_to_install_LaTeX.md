---
title: "What is the correct way to install LaTeX?"
date: 2007-01-29
forum: General Help
---

### Post by gwinn on 2007-01-29
Hi. I'd like to install LaTeX on Ubuntu Version 6.06 LTS. I've tried running the Synaptic Package Manager and installing everything that looks TeX related, however, even after that, if I try to process a .tex source file (one that works fine on other systems) I get error messages reporting that xcolor.sty isn't available. Is there some documentation somewhere on how to install a complete LaTeX system?

Thanks in advance.

Geoff.

---

### Post by schilcha on 2007-01-29
Did you install the package latex-xcolor? I have and I can process a latex-file that does a "\usepackage{xcolor}" without problem.

---

### Post by WW on 2007-01-29
You have probably already discovered that the basic packages for latex are **tetex-bin**, **tetex-base**, and **tetex-extra**, but there are more tex-related packages that you might find useful.  Most of them are in the universe repository.  As schilcha pointed out, xcolor.sty is provided by **latex-xcolor**.  Take a look here for more: [http://packages.ubuntu.com/dapper/tex/](http://packages.ubuntu.com/dapper/tex/)

---

### Post by gwinn on 2007-01-30
Thank you for that. The underlying problem was that I hadn't defined enough repositories to the packafe manager. Given your prompt I can now see lots more latex packages, including latex-xcolor so I think I'm all set.

Thanks again.

Geoff.

---

