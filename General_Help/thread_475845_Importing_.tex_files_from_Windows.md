---
title: "Importing .tex files from Windows"
date: 2007-06-16
forum: General Help
---

### Post by Lioness on 2007-06-16
Hi, I recently switched over to using Ubuntu (Feisty Fawn x86_64 version) and have an undergraduate honors thesis in progress that I've begun in Windows (using miktex and texniccenter) and I need to be able to edit it now. I installed the newest versions of Texlive and Texmaker using a guide [here]("http://doc.gwos.org/index.php/TeXLive_and_Texmaker") and am able to build it, however the files still try to pull the packages from the directory where MiKTeX was in Windows and obviously do not succeed in such. No error message is given, just a blank .pdf is generated from this mess. 

I'm not sure where to start in identifying the problem and how to go about fixing it. Is there anyone here who can maybe provide a little bit of guidance to a noob?

---

### Post by Old *ix Geek on 2007-06-17
DISCLAIMER: I know absolutely nothing about any of the applications you're referring to!
> the files still try to pull the packages from the directory where MiKTeX was in Windows
Perhaps recreating the directory structure would work?  Or is there not some way within the software to change where it's looking for the files?

---

### Post by Lioness on 2007-06-18
> **Old *ix Geek said:**
> DISCLAIMER: I know absolutely nothing about any of the applications you're referring to!

Perhaps recreating the directory structure would work?  Or is there not some way within the software to change where it's looking for the files?

Not that I could find. The odd thing is that I've never had this program reference miktex at all, so it has to be in the code somewhere but the code is transferred from another PC with a different directory structure and had no problems like this integrating into my copy of Windows. I've recently removed Windows from this laptop so I've got to find a way to handle this in Ubuntu so I don't have to install tons of bloat (Vista) just to use LaTeX which should work fine in a Linux environment. 

Thanks for trying to help though. I appreciate the response.

---

### Post by frisket on 2007-06-28
The only reason why LaTeX would be looking in Win-specific places for files is because your document (or modified class files or package files) say so. If I have (say) \usepackage(setspace) then LaTeX (any platform/distro) will get that from wherever it's kept on that platform/distro. It won't look for C:\Program Files\MiKTeX 2.5\miktex\something if you're running Linux unless you have done something to hard-code Windows filespecs into your code.

Can you post a minimal example and log file somewhere that illustrates the problem?

---

