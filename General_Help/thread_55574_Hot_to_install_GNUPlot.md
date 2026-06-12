---
title: "Hot to install GNUPlot?"
date: 2005-08-09
forum: General Help
---

### Post by ferhat00 on 2005-08-09
I have tried installing GNUPlot but it does not seem to work. The application loads find, and I can run it, but when I want to plot say a simple groph like y=sin(x) for test purposes, nothing happens or is displayed. Anyone else have these problems? I am missing some additional packages that GNUPlot requires? If so, which ones? I would appreciate if you could give me a detailed description for the installation procedure as I am a Linux newbie. Many thanks. O:)

---

### Post by varunus on 2005-08-09
You should be able to get all the info you need from "man gnuplot" in a terminal.

Generally, you should use octave with GNUplot if you want to make things easy.  Octave is an open source matlab clone that follows matlab syntax exactly and is compatible with most matlab programs.  You can get it through universe; octave will let you plot commands easily, it calls GNUplot when you do so.

---

