---
title: "Firefox problem with pdf files"
date: 2007-03-28
forum: General Help
---

### Post by buttari on 2007-03-28
Hi,
until a few days ago, when clicking on a pdf file I had the choice between saving the file on disk or opening it with evince. Now I don't have the choice anymore: firefox only wants to save pdf files. Does anybody have an idea of what happened and (possibly) how to solve the problem?
Thanks

Alfredo

---

### Post by fanatik on 2007-03-28
You could try removing the action for PDF's... 

In Firefox:
Edit->Preferences->Content->Manage
Highlight the PDF line and click Remove then Close.

See if that cures it.

James.

---

### Post by buttari on 2007-03-28
> **fanatik said:**
> You could try removing the action for PDF's... 

In Firefox:
Edit->Preferences->Content->Manage
Highlight the PDF line and click Remove then Close.

See if that cures it.

James.

Hi James,
there's no PDF line in my Edit->Preferences->Content->Manage menu.

Alfredo

---

### Post by noynac on 2007-03-28
> **buttari said:**
> Hi James,
there's no PDF line in my Edit->Preferences->Content->Manage menu. Alfredo

I had the same problem as you--when I clicked on a link to a PDF document in Firefox, the file would download rather than open in Evince. And, like you, I did not have a PDF line in the Firefox content-manage menu.

I spent some time trying to fix this but never found a real solution. I finally installed the "PDF Download" extension, which gives you various options when you click on a link to a PDF file. Unfortunately, it doesn't always work as it's supposed to, but it's better than nothing.

---

### Post by buttari on 2007-03-28
> **noynac said:**
> I had the same problem as you--when I clicked on a link to a PDF document in Firefox, the file would download rather than open in Evince. And, like you, I did not have a PDF line in the Firefox content-manage menu.

I spent some time trying to fix this but never found a real solution. I finally installed the "PDF Download" extension, which gives you various options when you click on a link to a PDF file. Unfortunately, it doesn't always work as it's supposed to, but it's better than nothing.

Hi noynac,
well, this is quite annoying. As a policy I tend to avoid installing stuff as much as possible. Since I planned to go for a fresh install when Feisty will come out, I have to suffer this problem only for few more days. Probably I'll spend some time trying to fix it. I'll let you know if I find a solution.
Thanks

Alfredo

---

### Post by noynac on 2007-03-28
I would appreciate any solution that you find. 

As an aside, during my previous research on this issue, some people suggested that the problem has to do with the mimeTypes.rdf file. The following site raises this issue:

[http://tinyurl.com/24tg6b](http://tinyurl.com/24tg6b)

I was busy with other things and never spent additional time on this. Also, I'm new to Linux and figured I might do more harm than good.

---

### Post by buttari on 2007-03-28
> **noynac said:**
> I would appreciate any solution that you find. 

As an aside, during my previous research on this issue, some people suggested that the problem has to do with the mimeTypes.rdf file. The following site raises this issue:

[http://tinyurl.com/24tg6b](http://tinyurl.com/24tg6b)

I was busy with other things and never spent additional time on this. Also, I'm new to Linux and figured I might do more harm than good.

noynac,
I just removed the mimeTypes.rdf file and it started working again.

Alfredo

---

### Post by noynac on 2007-03-28
> **buttari said:**
> noynac,
I just removed the mimeTypes.rdf file and it started working again.
Alfredo

I'm glad that worked. I was concerned that deleting the mimeTypes file might break something else (e.g. flash), but I deleted the file after making a backup and everything seems to work. Let's hope it stays that way.

---

### Post by diatom300 on 2007-04-05
Hi, I also had this problem. 

If you don't want to delete the mimeTypes.rdf file, open the file with gedit and search for the line containing RDF:about="urn:mimetype:handler:application/pdf" In the lines immediately below this change "NC:saveToDisk"  to "false" and change "NC:alwaysAsk" to "true". Save and exit. Next time you try to open a pdf in firefox it should ask you what you want to do.

---

