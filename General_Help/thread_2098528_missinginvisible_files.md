---
title: "missing/invisible files"
date: 2012-12-26
forum: General Help
---

### Post by uschmuntu on 2012-12-26
ok I just got some photos off my camera to sell some stuff on ebay.
But when I go to add the photos to the listing they are missing.
Photos and thumbnails are present in the file manager, but absent from within firefox. 
Restarting the browser makes no difference. Other photos are there, just not recent ones.  Is this a firefox problem? Surely the browser shouldn't be remembering what used to be in the folder?
I am running xbmcbuntu 11

---

### Post by fdrake on 2012-12-26
> **uschmuntu said:**
> ok I just got some photos off my camera to sell some stuff on ebay.
But when I go to add the photos to the listing they are missing.
Photos and thumbnails are present in the file manager, but absent from within firefox. 
Restarting the browser makes no difference. Other photos are there, just not recent ones.  Is this a firefox problem? Surely the browser shouldn't be remembering what used to be in the folder?
I am running xbmcbuntu 11
check the photo format. probably you have selcted a specific format. Changit to "ALL files" or something like that

---

### Post by uschmuntu on 2012-12-26
no, file format is correct, jpg. I am unable to choose "all files" which is normally an option in the folder windows.

Chromium web browser does not even display ebay's add photo option.

so I install yet another browser, epiphany, same problem.
what is going on with these web browsers?
[COLOR=#000000][FONT=Arial]how can it be that ebay is incompatible with linux or linux is incompatible with ebay?
why is it that ebay web site simply does not work on these "standards compliant" web browsers?

 How long should it take an ubuntu user to do one simple ebay listing?

[/FONT][/COLOR]

---

### Post by uschmuntu on 2012-12-27
It looks like the problem is with Flash which ebay uses for uploads. Behaviour is as if the files have an unsupported extenion and are filtered. Ebay is looking for image files and the file filter is clearly visible and includes the correct .jpg format. I can't imagine that there is anything special about these canon jpg's, but they are invisible and therefore cannot be selected while other jpg's in the same folder are visible. Flash bug? Firefox bug? Linux bug?

---

### Post by fdrake on 2012-12-27
> **uschmuntu said:**
> It looks like the problem is with Flash which ebay uses for uploads. Behaviour is as if the files have an unsupported extenion and are filtered. Ebay is looking for image files and the file filter is clearly visible and includes the correct .jpg format. I can't imagine that there is anything special about these canon jpg's, but they are invisible and therefore cannot be selected while other jpg's in the same folder are visible. Flash bug? Firefox bug? Linux bug?

```
cd "into the folder where the images are"
ls -l *.jpg
```
maybe there are some persission restrictions on the files.

---

### Post by uschmuntu on 2013-01-18
I have found the problem. All jpg images have extension JPG instead of jpg. What a complete joke!  So who is to blame, ebay? flash? Canon? Gpicview? gphoto2? Nautilus? Who is going to do someting about this embarrasing failure of linux to simply get a photo off a camera and onto a website? This looks so bad or linux, which can't tell there is an image there because of its case sensitive naming convention and the failure of software to take this into consideration. Hilarious to think that this problem can persist in the year 2013. The problem is so obvious, so predictable, so easy to account for, so stupid.

---

