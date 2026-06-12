---
title: "tetex problem"
date: 2005-05-04
forum: General Help
---

### Post by Markus78 on 2005-05-04
i have a problem with the output in german. the extra characters of the german language doesn't work and i don't know why. my code is

\documentclass[12pt,a4paper]{article}
\usepackage[german]{babel}
\usepackage[T1]{fontenc}
\usepackage[latin1]{inputenc}
\begin{document}
\tableofcontents
\section{\ Test1}
\subsection{\ Test2}

Überschrift
\end{document}

i have also tried: \usepackage[ngerman];
\usepackage{latin1}; \usepackage[latin1]{inputenc};
\usepackage{isolatin1}

greetings markus

---

### Post by ow50 on 2005-05-04
[http://www.ubuntuforums.org/showthread.php?t=31039](http://www.ubuntuforums.org/showthread.php?t=31039)

---

### Post by Markus78 on 2005-05-04
[QUOTE=ow50][http://www.ubuntuforums.org/showthread.php?t=31039](http://www.ubuntuforums.org/showthread.php?t=31039)[/QUOTE]

i have already tried the suggestions in this thread. somehow it doesn't work. thanks so far but i always do a search before i post :-)!

---

### Post by ow50 on 2005-05-04
If UTF-8 is your system locale and your latex files are UTF-8 encoded, you really should use utf8 instead of latin1, which is ISO-8859-1.

Try:
```
\documentclass[12pt,a4paper]{article}

\usepackage{ucs}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[german]{babel}

\begin{document}
Überschrift
\end{document}
```

Do you get some error messages in the output when you run latex on it?

---

### Post by drasko on 2005-08-21
Now that we are at it, Does anybody know any LaTeX package manager in Linux, simmilar to the one MiKTeX has?

Drasko

---

