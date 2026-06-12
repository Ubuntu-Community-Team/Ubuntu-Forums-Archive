---
title: "Extracting MSI files"
date: 2007-05-10
forum: General Help
---

### Post by elreteipos on 2007-05-10
Is there a way to extract MSI files?

---

### Post by Steve H on 2007-05-10
I presume you mean the Microsoft Installer files....I don´t know about extracting them, but you can install most msi files using WINE.

Are you trying to extract the contents for something specific? or do you mean install??

:)

---

### Post by shtraue on 2007-05-10
There's a too called [LessMSIerables](http://blogs.pingpoet.com/overflow/pubfiles/lessmsierables-20051110.zip).

---

### Post by elreteipos on 2007-05-10
> Are you trying to extract the contents for something specific?Yup. There's this Firefox extension that comes in a MSI package and I want to extract the XPI file and install it manually.> There's a too called LessMSIerables.So there's no native tool that can do the job? You mean that I have to use this Windows tool through Wine?

---

### Post by shtraue on 2007-05-10
I suppose you want to extract WMP plug-in for Firefox, is it so? It's the only thing that I've encountered so far, that comes in MSI (ffplugin.msi).

I don't think there are native Linux tools for MSI (what would be the point of them?), because MSI is specific to Windows only, and so it is a far far away stranger for Linux.

---

### Post by elreteipos on 2007-05-10
> **shtraue said:**
> I don't think there are native Linux tools for MSI (what would be the point of them?), because MSI is specific to Windows only, and so it is a far far away stranger for Linux.Again: I just need to *extract* the contents of the MSI package, I do not need to install them or anything like that. There's gotta be some tool that can extract them. Something like 7-zip perhaps?

---

### Post by shtraue on 2007-05-10
Well, here's another thing - [MSI Unpacker for Linux](http://www.jsware.net/jsware/msicode.php3#unplin), but still, you'll have to install Windows stuff through WINE, in order to use it.

And Oh, I've just noticed but it looks like you need .NET to run LessMSIerables.

Well, good luck with your endevours! (BTW if you want to, I can extract that MSI for you in Windows, and upload its contents for you)

---

