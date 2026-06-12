---
title: "How to stop NVU opening links?"
date: 2005-07-06
forum: General Help
---

### Post by gammyhand on 2005-07-06
I like NVU but the problem is that when I get a new mail notification from GAIM and click on open mail it opens NVU instead of opening firefox. Any ideas how to stop this annoying little quirk?

---

### Post by intangible on 2005-07-06
Is everything setup properly under **System->Preferences->Preferred Applications** ?

---

### Post by gammyhand on 2005-07-06
[QUOTE=intangible]Is everything setup properly under **System->Preferences->Preferred Applications** ?[/QUOTE]
 Good question I will check when I get home. I was not sure where I would be looking :)

---

### Post by gammyhand on 2005-07-06
[QUOTE=gammyhand]Good question I will check when I get home. I was not sure where I would be looking :)[/QUOTE]
 There are only three things under preferred apps...mail, web and terminal. All are set up fine :(

---

### Post by gammyhand on 2005-07-07
[QUOTE=gammyhand]There are only three things under preferred apps...mail, web and terminal. All are set up fine :([/QUOTE]
 So anyone know how to change the file association?

---

### Post by intangible on 2005-07-07
You've got me stumped here, I don't know how to change file associations for the http: protocol except where I mentioned :confused:

I have no idea how nvu could've taken over those links.

---

### Post by gammyhand on 2005-07-07
[QUOTE=intangible]You've got me stumped here, I don't know how to change file associations for the http: protocol except where I mentioned :confused:

I have no idea how nvu could've taken over those links.[/QUOTE]
 Me neither :( Thanks for trying though.

---

### Post by intangible on 2005-07-07
Open **Applications->System Tools->Configuration Editor** and then goto **desktop->gnome->url-handlers** and double check those, specifically **http** and **https**  ; You can also use **Edit->Find** and do a search for **nvu** and see if it's referenced anywhere, it's installed and used on my machine, but there is nothing that references it in the Configuration Editor (and I don't have your problem?).

---

### Post by gammyhand on 2005-07-07
[QUOTE=intangible]Open **Applications->System Tools->Configuration Editor** and then goto **desktop->gnome->url-handlers** and double check those, specifically **http** and **https**  ; You can also use **Edit->Find** and do a search for **nvu** and see if it's referenced anywhere, it's installed and used on my machine, but there is nothing that references it in the Configuration Editor (and I don't have your problem?).[/QUOTE]
 Ta, will have a look :)

---

