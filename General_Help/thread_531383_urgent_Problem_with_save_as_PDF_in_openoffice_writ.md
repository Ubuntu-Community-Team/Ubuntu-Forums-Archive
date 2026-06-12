---
title: "urgent: Problem with save as PDF in openoffice writer"
date: 2007-08-21
forum: General Help
---

### Post by karl_kashofer on 2007-08-21
Hi !

I just dist-upgraded a kubuntu dapper machine to feisty. Everything went smooth, but I seem to have a very annoying problem in oowriter now.

When I export a file via "export to pdf" the resulting pdf has lots of blanks inserted into all text that is bold (s  o it l  ooks like th  is). 
I have no idea why that happens, it does not happen on my other feisty box, however i need to fix it asap.

I have added kprinter to oowriter and tried to print into kprinter->pdf, but that looks just really bad, the text looks all bold and very badly rendered.

Would anyone know where to start ?

Thanks,
karl

---

### Post by Steve Fisher on 2007-08-21
Completely remove and reinstall OOo?

---

### Post by karl_kashofer on 2007-08-21
hmm, how would i do that ?

aptitude remove --purge openoffice.org

does only remove the package openoffice.org, not the numerous other openoffice packages.

---

### Post by stchman on 2007-08-21
> **karl_kashofer said:**
> Hi !

I just dist-upgraded a kubuntu dapper machine to feisty. Everything went smooth, but I seem to have a very annoying problem in oowriter now.

When I export a file via "export to pdf" the resulting pdf has lots of blanks inserted into all text that is bold (s  o it l  ooks like th  is). 
I have no idea why that happens, it does not happen on my other feisty box, however i need to fix it asap.

I have added kprinter to oowriter and tried to print into kprinter->pdf, but that looks just really bad, the text looks all bold and very badly rendered.

Would anyone know where to start ?

Thanks,
karl

I recommend a clean install of Ubuntu.  If you wish to completely uninstall OO then use the following command:

```

sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer

```

That will do it.

---

### Post by karl_kashofer on 2007-08-21
Hmm, i tried to remove all installed openoffice packages, but that would also uninstall kde-desktop....

Bugger, i am at my wits end.
Would like to do a clean install, but the box is 400km away....

Any other ideas about how to fix the pdf export in openoffice ?

Thanks for your help guys,
Cheers,
Karl

---

### Post by Hagar Delest on 2007-08-22
Are you sure the fonts are still available ? Perhaps some have been replaced at upgrade and are now substituted.

To check  it, create a new OOo document and check if you see it in the fonts drop-down list.

---

