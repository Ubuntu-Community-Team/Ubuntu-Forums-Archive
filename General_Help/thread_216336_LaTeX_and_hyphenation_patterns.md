---
title: "LaTeX and hyphenation patterns"
date: 2006-07-15
forum: General Help
---

### Post by Foucault on 2006-07-15
Hi everyone,
I was trying to write a couple of (english & greek) texts using latex, however I can't get LaTeX to load the hyphenation patterns for greek. I keep getting the warning:

```

/usr/share/texmf-tetex/tex/generic/babel/greek.ldf:0: No hyphenation patterns were loaded for(babel) the language `greek'(babel) I will use the patterns loaded for \language=0 instead. 

```

Searching around a bit I came across a config file in /var/lib/texmf/tex/generic which is telling me to take a look at /etc/texmf/language.d/ and then run **update-language**. Inside this directory I found two files **00tex.cnf** and **10tetex.cnf**. The latter included all the available hyphenation patterns and greek was already enabled. I tried running update-language again, however I got the same warning and of cource no hyphenation was present.

My test latex file was something like:
```

\documentclass[a4paper,12pt]{book}
\usepackage[english,greek]{babel}
\usepackage{ucs}
\usepackage[utf8]{inputenc}
\begin{document}
\selectlanguage{greek}
<GREEK TEXT HERE>
\end{document}

```

If my memory serves well, I can't remember having this problem back on Breezy (now using Dapper).
Any ideas on how to get the hyphenation working properly? :rolleyes:

---

### Post by Foucault on 2006-07-15
OK, I've got some progress here.
Googling around a bit more I found [this]("https://launchpad.net/distros/ubuntu/+source/tetex-base/+bug/36145"). Which is exactly my problem. However none of the proposed solutions worked. I've tried reconfiguring the package, reinstalling the package, purging and reinstalling the package, but NOTHING seems to work. Hyphenation is not working and I am only getting overfull boxes.

Also after running **fmtutil-sys --all** (as the workaround in the link suggested) the output is a bit strange and contains parts like
```

language        : patterns for nl not loaded
language        : patterns for en not loaded
language        : patterns for de not loaded
language        : patterns for da not loaded
language        : patterns for sv not loaded
language        : patterns for af not loaded
language        : patterns for no not loaded
language        : patterns for deo not loaded
language        : patterns for uk not loaded
language        : patterns for us not loaded
...
language        : patterns for fr not loaded
language        : patterns for es not loaded
language        : patterns for ca not loaded
language        : patterns for it not loaded
language        : patterns for la not loaded
language        : patterns for pt not loaded
language        : patterns for ro not loaded
...
language        : patterns for pl not loaded
language        : patterns for cz not loaded
language        : patterns for sk not loaded
language        : patterns for hr not loaded
language        : patterns for sl not loaded
...
language        : patterns for tr not loaded
...
language        : patterns for gr not loaded
...
language        : patterns for fi not loaded
language        : patterns for hu not loaded
language        : patterns for vn not loaded

```

The strange is that a bit after it tells me that a couple of patterns are loaded (en,de,fr,it,.. and of course **not** greek). It seems that some patterns are not loaded (including greek) although they are not commended in the configuration files. Of course the required hyphenation file (grhyph.tex) is present.

I could really use some help here
Thank you in advance

---

### Post by rplantz on 2006-07-16
Sorry, all I can offer is that I was able to fix English:
[http://www.ubuntuforums.org/showthread.php?t=182771](http://www.ubuntuforums.org/showthread.php?t=182771)

---

