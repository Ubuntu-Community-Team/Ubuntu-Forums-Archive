---
title: "Visual Studio Code Problem."
date: 2022-02-12
forum: General Help
---

### Post by damirx on 2022-02-12
Hi,

Due to college I am using Visual Studio Code 1.64.2. Sometimes when I want to rename a file inside a java project, it does automatically rename the class. But some other times my PC freezes at this prompt "Extension 'Language Support for Java(TM) by Red hat" wants to make refactoring changes with this file move. 

At that point I cannot select anything and have to hard restart my PC.

Any ideas?

Thanks in advance.

---

### Post by #&amp;thj^% on 2022-02-12
About a year ago this worked for me:
I commented on the bug:
I can confirm that removing ~/.config/Code/User/workspaceStorage/ (I'm on linux) works! after removing that and starting code, completion works immediately.
Back-up any work you have started.
Let me know how it worked for you.

---

### Post by damirx on 2022-02-13
Hi 1fallen.

Thank you very much. It did work. Now I can rename the .java file as many times as I want.

I appreciate it. 

Kind regards.

---

### Post by #&amp;thj^% on 2022-02-14
Happy to help. :)
Might help others as well if you were to mark it as Solved, if satisfied.

---

