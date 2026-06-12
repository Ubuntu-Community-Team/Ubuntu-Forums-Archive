---
title: "Wrong language settings for MS fonts in  OpenOffice"
date: 2007-07-24
forum: General Help
---

### Post by wch on 2007-07-24
I have two very strange problems with OpenOffice.  The first problem is that when I go to the dialog box for changing character formatting or for changing paragraph styles, when I select one of the MS fonts (like Arial,  Times New Roman, Trebuchet MS), instead of seeing Italic, Bold, and Bold Italic, I see Cursiva, Negreta, and Negreta Cursiva.  It looks like some sort of language mixup.  All of the other fonts that I've looked at show the normal Italic and Bold options.  This problem happens only in OpenOffice; in AbiWord, it comes up as Italic, Bold, and Bold Italic.

I think it's causing a problem because my paragraph styles expect to see Times New Roman Italic, but that doesn't exist, so it shows an italicized sans serif font.

Here's the other weird thing: about half of the time, when the dialog box comes up, instead of the normal long list of fonts, I see only the following:
AR PL ZenKai Uni
Baekmuk Batang
Baekmuk Dotum
Baekmuk Gulim
Baekmuk Headline
Kochi Gothic
Kochi Mincho

I've done the following:
- Made sure the Gnome language setting is set to US English.
- Completely uninstalled OpenOffice and reinstalled, using Synaptic. 
- Completely uninstalled msttcorefonts and reinstalled, using Synaptic.
- Did 'rm -rf ~/.openoffice.org2'

None of these had any effect on the problem.  Does anyone out there have an idea of how to fix this?

---

