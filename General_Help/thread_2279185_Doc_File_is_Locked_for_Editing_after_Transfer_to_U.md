---
title: "Doc File is Locked for Editing after Transfer to Ubuntu"
date: 2015-05-21
forum: General Help
---

### Post by held7over on 2015-05-21
Using gFTP as the transfer app, I transfer updated files from my computer (Linux Mint Cinnamon 17.1) to my wife's Laptop (Ubuntu 14.04-2), since my computer keeps the master copy of the files she refers to in her occupation.

However, when she tries to open a Libre-Office Word document on her Laptop, she now gets the following error:

Document File <the name of the document> is Locked for Editing by my own User Name and the date I made the last mass update transfer.

She is then given a choice of opening in Read-Only mode or opening another Copy. However, if she picks either one of these options, she gets the following error:

General Error
General input/output error

Looking at the permissions on the file via GUI, reveals nothing as her own User Name is still the owner and she has full rights over the files, and the same is revealed from the commandline ls -l view.

How do I unlock all the Libre-Office documents I send her via gFTP?

---

### Post by dragonfly41 on 2015-05-21
If you inspect the folder where you have the master file .. and view "hidden files" .. you may see a .lock file which was created while editing a LibreOffice file.

If LibreOffice is closed  properly this .lock file disappears.

I use Krusader as my file navigator (installed from Ubuntu Software Centre) and I can go to View > Show Hidden Files when inspecting file system.

So my guess is that files have not been properly closed before sending.

You could consider using a free service such as SpiderOak.com or Wuali to share such files.

---

### Post by held7over on 2015-05-21
Thanks dragonfly41!

With that bit of information, I was able to solve the problem. Evidently I must have had that particular doc open when I did a transfer to her machine. I tried simply deleting the lock file, but that immediately gave me the second error I mentioned in my first write up when I double clicked the doc file on her machine. So I deleted her doc and re-transferred again the copy from my own machine, first making sure there was no lock file now present on my machine. 

Problem solved!  ):P

---

