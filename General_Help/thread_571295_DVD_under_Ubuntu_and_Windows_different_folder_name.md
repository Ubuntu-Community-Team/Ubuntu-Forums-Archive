---
title: "DVD under Ubuntu and Windows different folder names"
date: 2007-10-09
forum: General Help
---

### Post by joneZ on 2007-10-09
Hi,

I have a strange problem with a DVD. I burnded some files from my Ubuntu computer with brasero.
I gave this CD to a colleagues who is using windows.

Now all the foldernames are different. 8 characters only and files are also renamed.

It doesn't matter if I click, "Windows Compatibility modus" in brasero. 


But when I put in the  DVD in my computer everything looks fine. 


Could someone tell me wich File Format brasero is using. 

I think it is some kind of UDF or Joliet or other windows error.. That windows can't convert 
the foldernames correctly.


Greetings
Erik

---

### Post by por100pre1 on 2007-10-09
> **joneZ said:**
> 
It doesn't matter if I click, "Windows Compatibility modus" in brasero. 


I should matter, it is a bug. Use k3b instead:

```
sudo aptitude install k3b
```

---

