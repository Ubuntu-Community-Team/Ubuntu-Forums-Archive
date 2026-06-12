---
title: "Another AbiWord spellchecking problem..."
date: 2006-12-02
forum: General Help
---

### Post by gejr on 2006-12-02
Ok, I wasn't sure where to put this question so I'll try here.

I've searched everywhere for a way to change the default spellcheck in AbiWord. Can't believe this has to be so hard. I have uninstalled all aspell-packages, then reinstalled aspell and aspell-no (which is the language I'd like to have as default.) Now when I restart AbiWord I get no spellchecking at all. 

Going to "Tools -> Set Language" shows me that "English (US)" is default. How do I change this? I can set the language manually to Norwegian and everything will work perfectly, but the next time I start AbiWord I'll have to do the same again, for every document I open. Isn't that a bit retarded?

---

### Post by gejr on 2006-12-02
As usual I find the answer to my own question minutes after I finally post a question here.. 

The solution I found was to open /usr/share/AbiSuite-2.4/templates/normal.awt and change two references for "lang:en-US" to "lang:nb-NO"

A list over other possible lang-values can be found here:
[http://web.mit.edu/abiword_v2.4.5/.share.sun4x_510/AbiSuite-2.4/AbiWord/help/en-US/info/infospelling.html]("http://web.mit.edu/abiword_v2.4.5/.share.sun4x_510/AbiSuite-2.4/AbiWord/help/en-US/info/infospelling.html")

---

