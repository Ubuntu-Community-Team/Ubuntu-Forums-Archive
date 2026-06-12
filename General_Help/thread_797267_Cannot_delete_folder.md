---
title: "Cannot delete folder"
date: 2008-05-17
forum: General Help
---

### Post by Ramptu on 2008-05-17
I accidently dragged the desktop icon from the Places menu unto my desktop. It created a desktop folder on the desktop so I sent it to the trash and cannot delete it from the trash folder. When I browse the desktop folder inside the trash it contains a desktop folder which contains a desktop folder etc... Anyway to delete this?

---

### Post by dcstar on 2008-05-17
> **Ramptu said:**
> I accidently dragged the desktop icon from the Places menu unto my desktop. It created a desktop folder on the desktop so I sent it to the trash and cannot delete it from the trash folder. When I browse the desktop folder inside the trash it contains a desktop folder which contains a desktop folder etc... Anyway to delete this?

Open you home folder in Nautilus, and find the hidden ".Trash" folder, go into that and delete its contents.

---

### Post by chrisccoulson on 2008-05-17
I would seriously consider opening a bug report on Launchpad. I've just tried it and it does attempt to create a folder with infinite depth

---

### Post by Ramptu on 2008-05-17
When I go to Places>Home and select view hidden files I see no ".Trash" folder. I even tried to search for it. When I click on my trashcan icon I get this in the url bar "trash:///". The first time I tried to delete it it seemed to be deleting a bunch of stuff. It must be some sort of bug. I tried repeating the mistake and now I have 2 Desktop folders I cannot delete. Any ideas?

---

### Post by Ramptu on 2008-05-18
Still having this problem. I do not see a .Trash folder. Should I create one?

---

### Post by plucky on 2008-05-19
If you are running Hardy Heron i.e Ubuntu 8.04 your Trash folder is now located at ```
home/[color=red]yourusername[/color]/.local/share/Trash/files
```


Good Luck

---

### Post by Joeb454 on 2008-05-19
> **plucky said:**
> If you are running Hardy Heron i.e Ubuntu 8.04 your Trash folder is now located at ```
home/[color=red]yourusername[/color]/.local/share/Trash/files
```


Good Luck

Alternatively (if you are doing it from a terminal) you can use the following path: ```
~/.local/share/Trash/files
``` Just throwing that out there :)

---

