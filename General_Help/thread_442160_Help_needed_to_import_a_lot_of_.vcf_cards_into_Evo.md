---
title: "Help needed to import a lot of .vcf cards into Evolution"
date: 2007-05-13
forum: General Help
---

### Post by lamadredelsapo on 2007-05-13
I have all my e-mail contacts in .vcf cards and I need to import them into evolution. The program has a wizard that allows you to import one vcf at a time, but I would like to import them all at the same time, because there are quite a few contacts (~200 .vcf cards).

Is there any way to do this?

---

### Post by laidback on 2007-05-13
Although I've never used it Evolution says it can import .vcf files. Maybe you can simply hand it the entire file.

File>Import...at splash screen select single file and follow the wizard.

---

### Post by lamadredelsapo on 2007-05-13
They are a lot of separate .vcf files. I tried joinning them into a single .vcf file and importing that single file, but it doesn't work. It looks like I have to import them one by one.

Any ideas?

---

### Post by laidback on 2007-05-13
Oh I see. How about exporting to csv, merge those text files and then import into Evolution.

---

### Post by lamadredelsapo on 2007-05-13
Drag and drop is not working, which is a pitty

---

### Post by laidback on 2007-05-13
Can you export to text?

---

### Post by lamadredelsapo on 2007-05-13
Solved! All I had to do is merge all .vcf files into one big .vcf and import it. Thanks for the tips

---

### Post by ubrox on 2008-04-14
how do u merge them?

---

### Post by Yeti can't ski on 2008-04-24
Hi Lamadredelsapo,

I am posting below the same answer I left on this other thread: 

[http://ubuntuforums.org/showthread.php?t=45030&highlight=evolution+import+contacts](http://ubuntuforums.org/showthread.php?t=45030&highlight=evolution+import+contacts)

Let me know if it solves your problem. Regards. 


Yeti

Re: how to import multiple vcf files in evolution? 
________________________________________
I believe you ended up with 50 vcards because you couldn't import properly a ".csv" file from Outlook, right? 

I had that problem and found a dumb non-brilliant non-geek way of solving it. 

In several forums I read the suggestion of first installing Mozilla in the Windows system to do a conversion of the “.CSV” file, but that seemed too troublesome. Indeed, Gmail will easily do the same trick.

- Export your contacts from Outlook to as a regular ".CSV" file;
- Import those contacts into Gmail (in webmail mode);
- Export from Gmail to a ".VCF" file (it will be a single file); and finally
- Import ".VCF" file to Evolution. 

The "bonus" is that Gmail will automatically cancel doubled/repeated entries. Really great. I hope someday Evolution will do all that by itself.

If instead you absolutely cannot go back to Outlook to produce a ".CSV" file and reaaally must use the 50 vcards then you could give a try on one of those vcard organizers software for (argh!) Windows. Or, it may be the case to add each card individually to Evolution.  

Good luck.

---

