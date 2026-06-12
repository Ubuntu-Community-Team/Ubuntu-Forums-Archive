---
title: "Regarding copy and paste the text in xmgrace"
date: 2017-12-07
forum: General Help
---

### Post by dilip.h.n on 2017-12-07
[COLOR=#242729][FONT=Arial]I have a graph in xmgrace (say, a graph of 10 different concentrations and hence 10 lines of different color), and I have typed some text corresponding to define what does each line represent. But now I have another similar graph and want to copy the same text typed for the previous graph to the new one.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How to copy and paste the text typed in the xmgrace from one graph to another.[/FONT][/COLOR]

---

### Post by oldos2er on 2017-12-07
I can't find that program in the repositories; would you please tell us which version of Ubuntu you're running,  and how you installed xmgrace?

---

### Post by dilip.h.n on 2017-12-07
I am using Ubuntu 14.04 
and i installed grace through ubuntu software centre

---

### Post by Holger_Gehrke on 2017-12-07
A quick google for "xmgrace copy and paste" led me to a [wiki from a French university]("http://lptms.u-psud.fr/wiki/index.php/Tips_for_Xmgrace"). Seems like xmgrace is an old Motif Application. Back then you marked things for copying with the left mouse button and pasted them with the middle mouse button. According to the wiki you can't paste text directly from one box to the other. You have to have a terminal open to put your copied text temporarily because the mark gets lost when you switch to a new box. Another approach: use a text editor. The files grace saves are supposedly plain text, so you should be able to copy and paste in an editor and then check the results by loading the changed files into grace again.

And it seems grace isn't in the repositories anymore on 17.04 either. There's a ppa for it on launchpad offering version 5.1.

Holger

---

