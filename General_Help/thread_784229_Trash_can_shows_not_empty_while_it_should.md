---
title: "Trash can shows not empty while it should ?"
date: 2008-05-06
forum: General Help
---

### Post by showgun22 on 2008-05-06
Hardy Heron 
I have use right clicking to empty the trash and it still shows not empty I have tried using Nautilus but than the trash shows empty. But back on Desktop it is not.

If I delete something and empty trash it works for the file I deleted but not for the one that still shows in the trash.

I have tried many things I have read but I have not been able to cd to the trash at the command line..
I welcome any help on this thanks

---

### Post by perlluver on 2008-05-06
> **showgun22 said:**
> Hardy Heron 
I have use right clicking to empty the trash and it still shows not empty I have tried using Nautilus but than the trash shows empty. But back on Desktop it is not.

If I delete something and empty trash it works for the file I deleted but not for the one that still shows in the trash.

I have tried many things I have read but I have not been able to cd to the trash at the command line..
I welcome any help on this thanks

Take a look in ./local/share/trash/files, press control-h in your home folder to view the hidden folders.  If they are there, use sudo nautilus, press alt-f2 and enter that command, then find that folder again.

---

### Post by showgun22 on 2008-05-06
Thanks it is a done thing now that I was able to locate the trash can I was able to delete the file at the command line....
Again thanks you

---

### Post by perlluver on 2008-05-06
> **showgun22 said:**
> Thanks it is a done thing now that I was able to locate the trash can I was able to delete the file at the command line....
Again thanks you

No problem, had this same problem, and was tearing my hair out.

---

### Post by showgun22 on 2008-05-06
From what I recall lots of the post I had read were saying rm -rf ~/trash/*

Or something similar but I was getting error with the bash cd command and I am now realizing the ~ meant the path to the trash folder ..
Oh well life is a continuous learning experience mostly for us Ubuntu newbie..<BG>

It is a very good thing you put the complete path to the trash otherwise I would still be lost...<BG>

---

