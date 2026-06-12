---
title: "Japanese character in LaTeX"
date: 2008-02-13
forum: General Help
---

### Post by MadMage on 2008-02-13
Hi all,
I have an english-based installation of Kubuntu 7.10. I have support for Japanese characters, which I am able to write in vim or kwrite.

Now I want to use some Japanese characters in my LaTeX documents, I know it is possible, but I cannot figure out how.

What I want is something like this:
...
\begin{document}
This are not japanese characters, &#26085;&#26412;&#35486;, so you see that they are mixed.
\end{document}

I installed:
latex-cjk-japanese
latex-cjk-japanese-wadalab
latex-ucs

But when I write Japanese characters in a LaTeX file, it simply ignores them.

---

### Post by lars512 on 2008-02-23
Ok, there's two issues here. Firstly, you need the correct LaTeX in your document to output CJK characters. Secondly, you need to have a font installed. I'm not sure why it doesn't work out of the box with wadalab (or perhaps it does, for Japanese only), but there's instructions included on how to install it all yourself. [I also wish they just made a package!]

In terms of having the correct LaTeX code, take a look at /usr/share/doc/latex-cjk-common/examples/UTF8.tex:
```
\documentclass[12pt]{article}

\usepackage{CJKutf8}
\usepackage[T1]{fontenc}

% we want the Unicode font for normal text also
\DeclareFontFamily{T1}{song}{}
\DeclareFontShape{T1}{song}{m}{n}{<-> cyberbit00}{}
\renewcommand\rmdefault{song}

\begin{document}

\begin{CJK}{UTF8}{song}

\noindent Hello World!

\noindent &#922;&#945;&#955;&#951;&#956;&#941;&#961;&#945; &#954;&#972;&#963;&#956;&#949;

\CJKnospace
\noindent &#12371;&#12435;&#12395;&#12385;&#12399; &#19990;&#30028;

\end{CJK}
 
\end{document}

```

The key parts are the first block, between \documentclass and \begin{document}. Every Japanese document will need something like that to set the mode as UTF8 (if that's what you're using) and to set the font correctly. Even then you still need to write your CJK characters in between the \begin{CJK}{UTF8}{song} and \end{CJK} tags.

Copy the file into a directory, then run pdflatex on it. Does it work? If there's errors, probably the cyberbit font is missing. You'll need to follow the steps under the heading **Cyberbit** in /usr/share/doc/latex-cjk-common/README.Debian.gz. I followed those listed as the "New way" and it worked. Let me know how you go, if you're still trying to get this working.

---

