---
title: "LaTeX in Gusty"
date: 2008-02-11
forum: General Help
---

### Post by Trurl on 2008-02-11
(This will solve any "Log File not Found" errors)

Ok, this is likely old hat for everyone, but I can't delete this thread and I just solved my problem, so here's a quick overview for anyone else trying to get latex working in ubuntu--Trurl style. Most of the information is actually on the Texmaker site, I just didn't bother to look up my problem there.

1. Using synaptic or terminal, download texlive and affiliated packages.

2. Similarly, download texmaker.

3. Restart X and log back in.

4. Create a test latex document

5. Save the document BEFORE compiling, and MAKE SURE to include the .tex in the filename.

6. Now compile. Should be all happy.

---

### Post by kalwisti on 2008-02-13
Trurl,

Thanks for posting this summary; it was not old hat to me and I found it very helpful. I am a new user of Feisty Fawn who wanted to get a working TeX / LaTeX installation as well as a front-end editor. From searching the forums, it appears that many people have switched to TeX Live rather than teTeX {+} and that installing Kile may be too problematic for a new Ubuntu user.

I followed your instructions and everything seems to be working smoothly. I think anyone who has used Kile will feel right at home with Texmaker; their GUIs are similar.  

{+}. For those who might not be aware of what happened to teTeX . . . In May 2006, Thomas Esser announced the end of support for teTeX, and recommended that users switch to TeX Live ( [http://www.tug.org/tetex/]("http://www.tug.org/tetex/") ). It's interesting that the other two distros I use (Xandros and PCLinuxOS) do not have TeX Live in their repositories and are still using teTeX (which works fine, BTW).

=david

---

### Post by spacefreak86 on 2008-02-14
Okay, this helped quite a bit, as I can now load the file as a .dvi or .ps file. But for some reason, it will not load the PDF file for it, claiming " Error : could not start the command" . I'm used to using TeXnicCenter in Windows, where there is a nice button that when pressed, will compile the document and output it to a .pdf file. Is there an equivalent in TeXMaker, and if so, how do I go about getting to it?

---

### Post by spacefreak86 on 2008-02-14
Nevermind, I had to change the PDF viewer to the acroread file for Adobe. Yay, I'm in business now  :)

---

