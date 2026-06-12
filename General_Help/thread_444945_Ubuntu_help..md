---
title: "Ubuntu help."
date: 2007-05-15
forum: General Help
---

### Post by Kodge on 2007-05-15
Id firstly like to appologise if this is in the wrong forum.

Ive recently partitioned my hard drive with ubuntu, Everything is working fine, I wanted to see how my game " World of Warcraft " would play. So I installed all the necessary programs I needed to run it. but then relised I only had 5.5gig left on the Ubuntu partition so I couldn't install the game. However I can reach my windows files via the Ubuntu partition. Is there anyway I can get wine to run World of warcraft from my windows part of the harddrive?


Sorry if this seems a stupid question, im new to all this linux jazz, everyone has to start somewhere right? :)

---

### Post by raja on 2007-05-15
Some programs run through wine even if they are accessed from a windows partition where they were installed. Some others dont and you have to install them through wine. I dont specifically know about wow - but you can give it a try. But remember that natively you wont have write access to your NTFS drives in Ubuntu.

---

### Post by Kodge on 2007-05-15
> **raja said:**
> Some programs run through wine even if they are accessed from a windows partition where they were installed. Some others dont and you have to install them through wine. I dont specifically know about wow - but you can give it a try. But remember that natively you wont have write access to your NTFS drives in Ubuntu.



Cheers for the heads up there Raja. But when I type " Wine WoW.exe " I get this

> wine: could not load L"c:\\windows\\system32\\wow.exe": Module not found

Its obviously looking in the wrong directory is there anyway I can direct it in the right way?

*edit* 

Well... I think its looking into the wrong directory, correct me if im wrong

---

### Post by raja on 2007-05-15
Navigate to the folder containing the .exe and then run it with wine from the terminal or right click on the exe and select "run with wine".

---

